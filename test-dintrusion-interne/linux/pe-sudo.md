# PE : sudo

### sudo -l

Connaître les commandes réalisable avec SUDO sans saisir de mot de passe :

```
sudo -l
```

Il est possible de connaître les binaires dangereux sur [https://gtfobins.github.io/](https://gtfobins.github.io).

_**Note :** selon les injections, réduire la taille du terminal après l'injection peut faire apparaitre le nouveau shell (par exemple quand le nouveau shell est dans un `man`)._

### CVE-2021-3156 (version de sudo 1.8.31)

La version 1.8.31 est vulnérable et permet à un attaquant d'élever ses privilèges. Un accès local est requis ([https://github.com/mohinparamasivam/Sudo-1.8.31-Root-Exploit](https://github.com/mohinparamasivam/Sudo-1.8.31-Root-Exploit)).
