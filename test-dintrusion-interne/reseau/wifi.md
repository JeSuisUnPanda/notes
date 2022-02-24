---
description: A finir
---

# WiFi

```
airmon-ng start wlan0
iwconfig
airdump-ng wlan0
airedump-ng --bssid <BSSID> -c <ID> -w wifi_output_<IP>.txt wlan0
aireplay-ng deauth 30 -a <BSSID> wlan0
```
