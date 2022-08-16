# LDAP

* Enumération LDAP anonyme :

```
ldapsearch -x -H ldap://<IP> -D '' -w '' -b "dc=domain,dc=local"
```

* Enumération LDAP avec un utilisateur :

```
ldapsearch -x -H ldap://<IP> -D '<domain.local>\<USER>' -w '<PASS>' -b "dc=domain,dc=local"
```
