# mysql

* Réaliser une connexion :

```
mysql -u <USER> -p
mysql --host=<IP> --user=<USER> --password=<PASSWORD <DB> -e "<MYSQL_COMMAND"
```

* Réaliser une commande en une ligne :&#x20;

```
mysql -u <USER> -p<PASSWORD> -D <DB> -e "<CMD>" > <FILE-OUTPUT>
```

* Lister les bases de données :

```
show databases;
```

* Choisir une base de données :

```
use <database>;
```

* Lister les tables :

```
show tables;
```

* Afficher le contenu d'une table :

```
select * from <table>;
```

* Ajouter du contenu dans une table :

```
insert into <table> (<field1>, <field2>, <...>) values (<value1>, <value2>, <...>);
```

* Exécuter des commandes système (requière une connexion + authentification valide) :

```
! ls -l
```
