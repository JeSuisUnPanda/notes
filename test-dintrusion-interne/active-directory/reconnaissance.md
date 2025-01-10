# Reconnaissance

### Énumération des utilisateurs

```
nxc smb <IP> -u '<USER>' -p '<PASS>' --users
```

Cette commande permet également de voir le champ "description" des utilisateurs.&#x20;

### Énumération des objets

Récupérer les objets de l'Active Directory :

```
sudo goddi -username=<USER> -password="<PASS>" -dc="<IP-DC>" -domain="<domain.local>" -unsafe
```

_Il est possible de lire facilement le résultat avec la commande suivante : `cat <file>.csv | cut -d "," -f <COL>`._

### Politique de mot de passe

```
cme smb <IP>/<MASK> -u <USER> -p <PASSWORD> --pass-pol
```

```
ldapdomaindump.py -u "<domain.local>\<USER>" -p <PASS> -n <DNS ou IP-DC> <IP-DNS>
```

### Nombre de machines qu'un utilisateur peut ajouter au domaine

```
ldapsearch -x -H ldap://<IP-DC> -b "DC=<DOMAIN>,DC=<LOCAL>" -D "<USER>" -W -s sub "(objectclass=domain)" | grep ms-DS-MachineAccountQuota

# Ajouter une machine au domaine (PowerShell)
add-computer -domain <DOMAIN.LOCAL>
```

### Bloodhound-python

```
bloodhound-python -u <USER> -p "<PASS>" -ns <IP-DC> -d <DOMAIN.LOCAL> -c all
bloodhound-python -u <USER> -p "<PASS>" -ns <IP-DC> -d <DOMAIN.LOCAL> -c Default
```

**Note :** _mettre `<IP-DC> <DOMAIN.LOCAL>` dans `/etc/hosts` peut supprimer des bugs. Parfois modifier l'option `-ns` par l'option `-gc` résous également des bugs. La commande `dig -x <IP-DC>` permet d'obtenir le nom du contrôleur de domaine._

Exemple de requêtes utiles sur `bloodhound` :&#x20;

```
# Droit dangereux d'utilisateurs sur d'autres objets (avec et sans privilèges)
MATCH (n:User) WHERE n.name =~ 'HELPDESK@DOMAIN.GR'MATCH (m) WHERE NOT m.name = n.name MATCH p=allShortestPaths((n)-[r:MemberOf|HasSession|AdminTo|AllExtendedRights|AddMember|ForceChangePassword|GenericAll|GenericWrite|Owns|WriteDacl|WriteOwner|CanRDP|ExecuteDCOM|AllowedToDelegate|ReadLAPSPassword|Contains|GpLink|AddAllowedToAct|AllowedToAct|SQLAdmin*1..]->(m)) RETURN p
MATCH (n:User {admincount:False}) MATCH (m) WHERE NOT m.name = n.name MATCH p=allShortestPaths((n)-[r:MemberOf|HasSession|AdminTo|AllExtendedRights|AddMember|ForceChangePassword|GenericAll|GenericWrite|Owns|WriteDacl|WriteOwner|CanRDP|ExecuteDCOM|AllowedToDelegate|ReadLAPSPassword|Contains|GpLink|AddAllowedToAct|AllowedToAct|SQLAdmin*1..]->(m)) RETURN p

# Droit dangereux utilisateur vers utilisateurs
MATCH (n:User {admincount:False}) MATCH (m:User) WHERE NOT m.name = n.name MATCH p=allShortestPaths((n)-[r:AllExtendedRights|ForceChangePassword|GenericAll|GenericWrite|Owns|WriteDacl|WriteOwner*1..]->(m)) RETURN p

# Droit dangereux utilisateur vers ordinateurs
MATCH (n:User {admincount:False}) MATCH p=allShortestPaths((n)-[r:AllExtendedRights|GenericAll|GenericWrite|Owns|WriteDacl|WriteOwner|AdminTo|CanRDP|ExecuteDCOM|ForceChangePassword*1..]->(m:Computer)) RETURN p

# Utilisateur pouvant s'ajouter dans des groupes
MATCH (n:User {admincount:False}) MATCH p=allShortestPaths((n)-[r:AddMember*1..]->(m:Group)) RETURN p
```
