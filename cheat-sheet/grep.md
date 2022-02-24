# grep

* Trouver un mot dans un nom de fichier d'une archive :

```
grep -a "word" file.zip
```

* Trouver un mot dans une archive .zip:

```
zipgrep "TOKEN_SECRET" files-port80.zip
```

* Trouver un mot de manière récursive dans répertoire :

```
grep -R "word"
```

* Trouver un mot sans se soucier de la _case_ :

```
grep -i "word"
```
