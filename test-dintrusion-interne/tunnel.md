# Tunnel

Lorsqu'un port est exposé localement sur une machine distante (`Listent 127.0.0.1:<PORT-LOCAL-MACHINE-DISTANTE>`), il est tout de même possible de le joindre depuis sa propre machine d'attaque.

### SSH

```
#Commande à exécuter sur la machine d'attaque
ssh -L <PORT-LOCAL-MACHINE-ATTAQUE>:localhost:<PORT-LOCAL-MACHINE-DISTANTE> <USER>@<IP>
```

Avec cette commande le `<PORT-LOCAL-MACHINE-DISTANTE>` de la machine `<IP>` sera joignable localement depuis la machine d'attaque sur le port `PORT-LOCAL-MACHINE-ATTAQUE>`.

#### Exemple

```
# Enumération sur le service
nmap 127.0.0.1 -p <PORT-LOCAL-MACHINE-ATTAQUE>

# Connexion ssh sur ce serive
ssh <USER>@127.0.0.1 -p <PORT-LOCAL-MACHINE-ATTAQUE>
```
