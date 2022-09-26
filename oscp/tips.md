# TIPS

### Enumération

* [ ] Chercher les CVE associées aux versions des technologies.

### Shell

* [ ] Quand un reverse-shell ne parviens pas à se connecter à la machine d'attaque, essayer des ports classiques.

### PE

#### Linux

* [ ] Regarder la version de l'OS : `uname -a`

#### Windows

* [ ] Analyser les privilèges : `whoami /priv` -> `SeChangeNotifyPrivilege` et `SeImpersonatePrivilege` sont `Enabled` = `LPE`

### Généralités

* Rechercher les versions avec 'site:github.com' ou 'site:exploit-db.com'.
