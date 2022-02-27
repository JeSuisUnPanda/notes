# find

### Recherche de fichiers

* Trouver les fichiers accessibles à l'utilisateur courant :

```
find / -type f -user $(whoami) 2>/dev/null | grep -v "/sys" | grep -v "/proc"
```
