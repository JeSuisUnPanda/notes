# RDP

### Réaliser une connexion

```
rdesktop <IP>
xfreerdp /u:<USER> /v:<IP>
```

#### Erreur connue

Résoudre le message d'erreur :

```
Failed to initialize NLA, do you have correct Kerberos TGT initialized ?
Failed to connect, CredSSP required by server (check if server disabled old TLS versions, if yes use -V option).
```

```
sudo apt-get install krb5-user
```

**Note :** _lors de l'installation, mettre le domaine en MAJUSCULE et l'adresse IP du contrôleur de domaine. Dans la commande `kinit` le domaine doit également être en majuscule._

```
kinit <USER>@<DOMAIN.LOCAL>
klist
rdesktop <IP>
```
