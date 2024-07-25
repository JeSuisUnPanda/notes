---
description: runas vs invoke-command ???
---

# runas

* Exécuter une commande avec les droits d'un autre utilisateur :&#x20;

```
runas /user:<USER> "<POWERSHELL_COMMAND"
```

* Exécuter une commande sur le domaine depuis une machine qui n'est pas inclue dans ce dernier :

```
runas /netonly /user:<DOMAIN.LOCAL>\<USER> <CMD> # Exemple snaffler.
```
