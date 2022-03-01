# Tunnel

### Accéder au port local d'une machine distance depuis son hôte

Lorsqu'un port est exposé localement sur une machine distante (`Listent 127.0.0.1:<PORT-LOCAL-MACHINE-DISTANTE>`), il est tout de même possible de le joindre depuis sa propre machine d'attaque.

```
# Commande à exécuter sur la machine d'attaque
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

### Utiliser les outils de son hôte sur une machine distante

```
# Mise en place du tunnel (Commande à exécuter sur la machine d'attaque)
ssh -D 9050 <USER>@<IP-MACHINE-DISTANTE>

# Exemple d'utilisation du tunnel
proxychains nmap <IP> # Permet de scanner les nouvelles machines accessibles
proxychains psql -h <IP-DB> -U <USER> -W # Permet de réaliser une connexion PSQL depuis la machine distante si l'accès n'est pas autorisé depuis l'hôte
proxychains ssh -D 9051 <USER>@<IP-MACHINE-DISTANTE-2> # Permet de réaliser un second tunnel. /!\ Modifier le port dans la configuration de proxychains (/etc/proxychains.conf) 
```
