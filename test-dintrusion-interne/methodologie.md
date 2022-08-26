# Méthodologie

### Analyse réseau

* [ ] Accès au réseau ([`ip`](../cheat-sheet/ip.md)`, cat /etc/resolv.conf`)
* [ ] Cartographie du réseau ([`nmap`](reseau/enumeration.md#enumeration-des-machines-+-services-nmap))
* [ ] Protocoles multidiffusion (`wireshark,`[`responder`](windows/protocoles-multidiffusion.md#llmnr))

### Analyse système

* [ ] Étude du niveau de mise à jour ([`goddi`](active-directory/reconnaissance.md#enumeration-des-objets)`,`[`cme`](windows/reconnaissance.md#version-de-los))
* [ ] Vulnérabilités connues ([`MS08_067`](windows/reconnaissance.md#ms08\_067)`,`[`MS17-010`](windows/reconnaissance.md#ms17-010)`,`[`BlueKeep`](windows/reconnaissance.md#bluekeep)`,`[`Zerologon`](windows/reconnaissance.md#zerologon))
* [ ] Sessions nulles ([`rpcclient`](reseau/rpc.md)`,`[`smbmap`](reseau/smb.md#enumeration-des-partages-reseau))
* [ ] Partages réseau ([`smbmap`](reseau/smb.md#enumeration-des-partages-reseau)`,`[`cme`](reseau/smb.md#enumeration-des-partages-reseau)`,`[`smbclient`](reseau/smb.md#enumeration-des-partages-reseau))
* [ ] Signature des échanges SMB ([`cme`](reseau/smb.md#signatures-smb))
* [ ] Mots de passe dans le champ "description" ([`goddi`](active-directory/reconnaissance.md#enumeration-des-objets)`, AdExplorer`)
* [ ] Politique de mot de passe ([`cme`](active-directory/reconnaissance.md#politique-de-mot-de-passe)`,`[`ldapdomaindump`](active-directory/reconnaissance.md#politique-de-mot-de-passe)`,`[`session Windows`](windows/reconnaissance.md#politique-de-mot-de-passe))
* [ ] Analyse des applicatifs (serveur web \[aquatone], serveur de base de données, etc.)
* [ ] Sécurité des équipements réseaux

### Exploitation de vulnérabilités

* [ ] NTLM Relay ([`responder`](active-directory/ntlm-relay.md)`,`[`impacket`](active-directory/ntlm-relay.md))
* [ ] Pass The Hash ([`cme`](windows/pass-the-hash.md))
* [ ] ASREPROAST (`bloodhound,`[`impacket`](active-directory/asrep.md))
* [ ] Kerberoast ([`impacket`](active-directory/kerberoast.md))
* [ ] Mots de passe faibles

### Post-exploitation

* [ ] Statistique sur les mots de passe (`impacket, hashcat,pipal`)

### WiFi

* [ ] Analyse du Wifi (`wifite`)

#### TIPS

* [ ] Password spraying dès qu'un mot de passe est trouvé (formulaires, utilisateurs système, services ouverts)
