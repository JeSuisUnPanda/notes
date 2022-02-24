# Reconnaissance

## Enumération des objets

Récupérer les objets de l'Active Directory :

```
sudo goddi -username=<USER> -password="<PASS>" -dc="<IP-DC>" -domain="<domain.local>" -unsafe
```

_Il est possible de lire facilement le résultat avec la commande suivante : `cat <file>.csv | cut -d "," -f <COL>`._

## Politique de mot de passe

```
cme smb <IP>/<MASK> -u <USER> -p <PASSWORD> --pass-pol
```

```
ldapdomaindump.py -u "<domain.local>\<USER>" -p <PASS> -n <DNS ou IP-DC> <IP-DNS>
```
