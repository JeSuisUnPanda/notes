# grep

* Trouver un mot et afficher celui-ci dans le terminal :&#x20;

```
grep -e "<WORD>"
```

* Trouver un mot de manière récursive dans répertoire :

```
grep -R "<WORD>"
```

* Trouver un mot sans se soucier de la _case_ :

```
grep -i "<WORD>"
```

* Trouver un mot dans un fichier mais afficher seulement le nom de ce fichier et la ligne :&#x20;

```
grep -nl "<WORD>"
```

* Trouver un mot dans un fichier de n'import quel type comme s'il s'agissait d'un fichier texte :

```
grep -a "<WORD>" <FILE>
```

* Trouver un mot dans une archive .zip:

```
zipgrep "TOKEN_SECRET" files-port80.zip
```
