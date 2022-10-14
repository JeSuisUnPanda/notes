# Méthodologie

## AD (suite à la compromission d'une machine)

Lancer le script `WinPEAS` et analyser le système avec les commandes suivantes :&#x20;

```
# Lister les utilisateurs locaux
net user

# Lister les utilisateurs du domaine
net user /domain

# Afficher les détails sur un utilisateur du domaine
net user jeff_admin /domain

# Lister les groupes du domaine
net group /domain

# Lancer Sharphound
./SharpHound.exe

# Est-ce qu'il y a des comptes Kerberoastable ?
### Attaque Kerberoast

# Est-ce qu'il y a des utilisateurs du domaine connectés à la machine ? (winPEAS)
### Tentative de dump leur mot de passe : sekurlsa::logonpasswords
### Tentative de dump leur ticket kerberos : sekurlsa::tickets

# Analyser la politique de mot de passe
net account
### Password Spraying

# Pass-The-Hash
```
