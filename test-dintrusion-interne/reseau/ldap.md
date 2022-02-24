# LDAP

* Enumération LDAP anonyme :

```
ldapsearch -x -h <IP> -D '' -w '' -b "dc=domain,dc=local"
```

* Enumération LDAP avec un utilisateur :

```
ldapsearch -x -h <IP> -D '<domain.local>\<USER>' -w '<PASS>' -b "dc=domain,dc=local"
```
