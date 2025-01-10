---
description: Utilisation de ticket Kerberos sur Linux
---

# Kerberos

Quand on obtient un ticket Kerberos, il est possible de l'utiliser avec `nxc` et `impacket`.

```
# Exemple de récupération d'un ticket
kinit <USER>@<DOMAIN.LOCAL> -> ça mets le ticket dans le fichier dans /tmp/krb5cc_1000

python3 gettgtpkinit.py -cert-pfx <FILE.pfx> -pfx-pass <PASS> <DOMAIN.LOCAL>/<USER> user.ccache -> ça mets le ticket dans le fichier user.ccache

# Exporter le fichier dans la variable  d'environnement
export KRB5CCNAME=<file>

# Vérifier que le ticket est importé 
klist

### nxc

nxc smb <IP> --use-kcache --shares
nxc smb <IP> --use-kcache --users

### Impacket (si impacket-*.py marche pas, utiliser *.py directement)

impacket-smbclient.py <DOMAIN.LOCAL>/<USER>@<COMPUTER-EN-MAJ>.<DOMAIN.LOCAL> -k -no-pass
```
