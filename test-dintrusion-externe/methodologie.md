# Méthodologie

### Découverte d'information

* [ ] Fuite d'informations (technologies, comptes, versions)
* [ ] Méta data
* [ ] Enumération (ports, ressources)
* [ ] Trouver les entrées utilisateurs

### Configuration

* [ ] Réaction de l'application face aux erreurs
* [ ] Langage utilisé
* [ ] Recherche d'anciens fichiers ou de fichiers par défaut
* [ ] Trouver les interfaces d'administration
* [ ] Cookies
* [ ] En-tête HTTP
* [ ] HTTPS

### Comptes utilisateur

* [ ] Création possible d'un utilisateur
* [ ] Lien d'activation
* [ ] Lien d'oublie de mot de passe
* [ ] Enumération des utilisateurs
* [ ] Politique de mot de passe
* [ ] Politique d'adresse mail
* [ ] Test des comptes par défaut ou triviaux

### Gestion des rôles

* [ ] Tester les droits des différents rôles
* [ ] Cloisonnement

### Accès aux ressources

* [ ] _Path Traversal_
* [ ] IDOR

### Gestion des session

* [ ] Valeurs sensibles dans les cookies
* [ ] Attaques sur les JWT
* [ ] CSRF

### Injections

* [ ] XSS
* [ ] LFI
* [ ] RFI
* [ ] XXE
* [ ] SQLI
* [ ] SSTI
* [ ] SSRF
* [ ] LDAPI
* [ ] XPATHI
* [ ] _Command injection_

### Attaques diverses

* [ ] _Open Redirect_
* [ ] Abus de fonction logique (temps de réponse, valeurs inattendues)

### Services exposés

* [ ] Comptes anonymes et triviaux
* [ ] Enumération

## TIPS

* [ ] Password spraying dès qu'un mot de passe est trouvé (formulaires, services ouverts)
