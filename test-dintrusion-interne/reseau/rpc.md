# RPC

* Enumération RPC anonyme :

```
rpcclient -U "" -N <IP>
```

* Enumération LDAP avec un utilisateur :

```
rpcclient -U "<USER>%<PASS>" -N <IP>
```

#### TIPS

* Enumérer les utilisateurs avec la commande `enumdomusers`.
* Enumérer les groupes avec la commande `enumdomgroups`.
