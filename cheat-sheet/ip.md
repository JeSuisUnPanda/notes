# ip

* Connaître ses adresses IP :

```
ip a
```

* Connaître ses routes :

```
ip route
```

* Ajouter une adresse IP :

```
sudo systemctl stop NetworkManager.service
sudo ip addr add <IP/MASK> dev eth0
```

* Changer d'adresse IP :

```
sudo ip addr flush dev eth0
sudo ip addr add <IP>/<MASK> dev eht0
```
