# TAP

Pour contourner le 802.1X, il est possible d'utiliser un TAP.

* Port 1 : commutateur ;
* Port 2 : victime ;
* Port 5 : attaquant.

```
sudo ip addr flush dev <INTERFACE>
sudo ip addr add <IP>/<MASK> dev <INTERFACE>
sudo ip route add default via <IP>/<MASK>
sudo macchanger -m <MAC> <INTERFACE>
```
