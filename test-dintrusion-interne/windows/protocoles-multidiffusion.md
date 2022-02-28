---
description: Comment casser les anciens hashs NTLM et lesquels sont relayables
---

# Protocoles multidiffusion

### LLMNR

```
sudo responder -I eth0 -vrd
sudo python3 Responder.py -I eth0 -rf
sudo python3 Responder.py -I eth0 --wpad
```

#### Comprendre les subtilités des résultats obtenus

Plusieurs types de _hashs_ peuvent être remontés par `Responder`. Voici les caractéristiques de chacun :

* NTLMv1 ou NTLMv2 : Correspond à un _hash_ émis par un serveur `Windows XP` ou `Windows Server 2003`.&#x20;
* NTLMv1-SSP ou NTLMv2-SSP : Correspond à un _hash_ émis par un serveur dont la version est plus récente que `Windows Server 2003`. SSP fait référence à SSPI qui signifie _Security Support Provider Interface._ Cette interface constitue la base de l’authentification Windows sur les serveurs récents.
