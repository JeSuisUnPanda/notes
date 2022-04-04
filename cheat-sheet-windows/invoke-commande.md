---
description: runas vs invoke-command ???
---

# invoke-commande

```
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
$p = ConvertTo-SecureString '<PASSWORD>' -AsPlainText -Force
$c = New-Object System.Management.Automation.PSCredential ('<USER>', $p)
invoke-command -computername localhost -credential $c -port 5986 -usessl -SessionOption $so -scriptblock {whoami}
```
