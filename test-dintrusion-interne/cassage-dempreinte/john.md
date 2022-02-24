# john

* Casser les _hashs_ d'une base SAM :

```
john –format=NT –wordlist=<FILE> hash.john
```

* Casser une clé GPG :

```
gpg2john key.priv > hash.john
john --wordlist=<FILE> hash.john
```
