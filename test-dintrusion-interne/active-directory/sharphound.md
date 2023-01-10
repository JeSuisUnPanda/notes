---
description: https://github.com/BloodHoundAD/SharpHound
---

# SharpHound

SharpHound est un script/exécutable qui permet d'avoir une représentation graphique d'un Active Directory.

```
# Si la machine est dans le domaine et que l'on a pas de session :
# Powershell
Powershell.exe -Exec Bypass
Import-Module .\Sharphound.ps1
Invoke-Bloodhound
Invoke-BloodHound -CollectionMethod All
```
