# telnet

## Envoyer un mail

```
telnet <IP> 25
[...]
MAIL FROM: <ADDR-PREFIX>@<ADDR-SUFFIX>
[...]
RCPT TO: <USER>@<DOMAIN.LOCAL>
[...]
DATA
<MESSAGE>

.
250 OK
```
