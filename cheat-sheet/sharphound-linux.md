# sharphound (linux)

### Récupération des informations sur un domaine

```
bloodhound-python -u <USER> -p "<PASS>" -ns <IP-DC> -d <DOMAIN.LOCAL> -c all
```

```
bloodhound-python -u <USER> -p "<PASS>" -ns <IP-DC> -d <DOMAIN.LOCAL> -c Default
```

**Note :** _mettre `<IP-DC> <DOMAIN.LOCAL>` dans `/etc/hosts` peut supprimer des bugs. Parfois modifier l'option `-ns` par l'option `-gc` résous également des bugs. La commande `dig -x <IP-DC>` permet d'obtenir le nom du contrôleur de domaine._
