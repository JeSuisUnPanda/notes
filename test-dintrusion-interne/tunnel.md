# Tunnel

## SSH

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

# Connexion ssh sur ce service
ssh <USER>@127.0.0.1 -p <PORT-LOCAL-MACHINE-ATTAQUE>
```

### Utiliser les outils de son hôte sur une machine distante (pivot)

```
# Mise en place du tunnel (Commande à exécuter sur la machine d'attaque)
ssh -D 9050 <USER>@<IP-MACHINE-DISTANTE>

# Exemple d'utilisation du tunnel
proxychains nmap <IP> # Permet de scanner les nouvelles machines accessibles
proxychains psql -h <IP-DB> -U <USER> -W # Permet de réaliser une connexion PSQL depuis la machine distante si l'accès n'est pas autorisé depuis l'hôte
proxychains ssh -D 9051 <USER>@<IP-MACHINE-DISTANTE-2> # Permet de réaliser un second tunnel. /!\ Modifier le port dans la configuration de proxychains (/etc/proxychains4.conf) 
```

## chisel

L'outil [chisel](https://github.com/jpillora/chisel) permet de faire un tunnel SOCKS entre un client et un serveur sur Linux et Windows. L'avantage par rapport aux tunnels SSH, c'est que les tunnels reposent sur un binaire. Ainsi, pas besoin que le service SSH soit actif.

### Accéder au port local d'une machine distance depuis son hôte

Les commandes suivantes permettent d'accéder au port 80 de la machine victime depuis la machine d'attaque en tapant sur le port local 8081.

```
# Sur la machine d'attaque 
./chisel server -p 8000 --reverse

# Sur la machine victime
./chisel client <IP-MACHINE-ATTAQUE>:8000 R:8081:127.0.0.1:80 permet de d'accéder au port 80 de la machine victime en tapant le port 127.0.0.1:8081 sur la machine de l'attaquant.
```

Dans le cas d'un port Web, il est même possible de voir le contenu dans Mozilla en accédant là l'adresse http://127.0.0.1:8081.

### Utiliser les outils de son hôte sur une machine distante (pivot)

Note : Utilisable quand la machine d'attaque ne peut pas joindre la machine victime.

```
# Sur la machine d'attaque 
./chisel server -p 8000 --reverse

# Sur la machine victime
./chisel client <IP-MACHINE-ATTAQUE>:8000 R:9050:socks

# Exemple d'utilisation du tunnel
proxychains nmap <IP>/<MASK> # Permet de scanner les nouvelles machines accessibles
proxychains psql -h <IP-DB> -U <USER> -W # Permet de réaliser une connexion PSQL depuis la machine distante si l'accès n'est pas autorisé depuis l'hôte
```

Il est possible d'afficher un service Web découvert par proxychains dans le navigateur Mozilla avec les paramètres suivants :&#x20;

* Manual proxy
* Socks : Host = 127.0.0.1 et port 9050
* Checkbox Socks v5 cochée&#x20;
* Checkbox Proxy DNS when using SOCKS v5 cochée
