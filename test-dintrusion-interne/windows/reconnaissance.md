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
```

#### MS17-010

```
nmap -v -p445 --script smb-vuln-ms17-010.nse
```

#### BlueKeep

```
msf > use auxiliary/scanner/rdp/cve_2019_0708_bluekeep
```

#### Zerologon

```
python3 zerologon_tester.py <DC> <IP-DC>
```
