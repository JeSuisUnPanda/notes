---
description: Logiciel de gestion de version
---

# svn

_**Note :** le `svn://` est obligatoire pour que les commandes fonctionnent._

* Copier localement les fichiers d'un dépôt :&#x20;

```
svn co svn://<IP> # Sans authentification
svn co --username <USER> svn://<IP> # Authentifié
svn co -r 2 svn://<IP> # Sélectionner une révision particulière
```

* Afficher les modification apportées au dépôt :&#x20;

```
svn log svn://<IP>
```
