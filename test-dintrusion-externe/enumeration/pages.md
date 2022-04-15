# Pages

* Enumérer en forçant les extensions :

```
python3 dirsearch.py -u "http://domain.com" -e ",php,html" -f 
```

* Enumérer avec un dictionnaire :

```
python3 dirsearch.py -u "http://domain.com" -e ",php" -f -w "/etc/list.txt"
```

* Enumérer en éxcluant des codes de retour :

```
python3 dirsearch.py -u "http://domain.com" -e ",php" -f -x 404
```

#### TIPS :&#x20;

* Enumérer sur une IP peut s'avérer plus rapide que sur le domaine. Attention à scanner le bon sous-domaine cependant.
