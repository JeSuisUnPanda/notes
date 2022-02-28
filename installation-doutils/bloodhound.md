# Bloodhound

### Solution 1

```
sudo apt-get install bloodhound
sudo neo4j console # http://localhost:7474 pour changer le mot de passe
bloodhound
```

### Solution 2

Prendre la version communautaire sur [https://neo4j.com/download-center/#community](https://neo4j.com/download-center/#community) en version 4.0.10. Cela va télécharger une archive.

Pour démarrer `neo4j`, exécuter la commande suivante dans `/neo4j-community-4.0.10/`:

```
sudo ./bin/neo4j console
```

Les identifiants de connexion par défaut sont `neo4j:neo4j`. Un nouveau mot de passe devra être soumis (`root`).

Prendre la version 4.0.1 sur [https://github.com/BloodhoundAD/Bloodhound/releases](https://github.com/BloodhoundAD/Bloodhound/releases). Cela va télécharger une archive.

Pour démarrer `Bloodhound`, réaliser la commande suivante dans `/Bloodhound-linux-x64/` :

```
sudo ./Bloodhound --no-sandbox
```
