---
description: Runs commands on local and remote computers
---

# invoke-commande

```
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
$p = ConvertTo-SecureString '<PASSWORD>' -AsPlainText -Force
$c = New-Object System.Management.Automation.PSCredential ('<USER>', $p)
invoke-command -computername localhost -credential $c -port 5986 -usessl -SessionOption $so -scriptblock {whoami}
```
