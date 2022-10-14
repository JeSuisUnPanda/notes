# TIPS

### Enumération

* [ ] Chercher les CVE associées aux versions des technologies.
* [ ] Essayer des mots de passe triviaux (possibilité d'ajouter un domaine s'il y en a un).

### Shell

* [ ] Quand un _reverse-shell_ ne parviens pas à se connecter à la machine d'attaque, essayer des ports classiques.

### PE

#### Linux

* [ ] Regarder la version de l'OS : `uname -a`.
* [ ] Regarder les groupes de l'utilisateur : `id` -> groupe `docker` -> `LPE`.

#### Windows

* [ ] Prioriser `winPEAS.exe` plutôt que `winPEASx86.bat`.
* [ ] Analyser les privilèges : `whoami /priv` -> `SeChangeNotifyPrivilege` et `SeImpersonatePrivilege` sont `Enabled` = `LPE`.

#### AD

* [ ] Essayer des dérivés de mots de passe pour trouver d'autres comptes.
* [ ] Essayer tous les comptes trouvés sur toutes les machines et sur tous les protocoles/services ouverts.
* [ ] Il est possible de réaliser un SharpHound depuis une machine du domaine (sans avoir à utiliser de compte du domaine)

### Généralités

* Rechercher les versions avec 'site:github.com' ou 'site:exploit-db.com'.
* Déposer les fichiers dans `/home` ou `/tmp`.
