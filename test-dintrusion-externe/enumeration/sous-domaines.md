# Sous domaines

* Enumérer les _Virtual-hosts_ :

```
gobuster vhost -u http://domain.com -w "/etc/list.txt" -k -t 20 | grep 200
```
