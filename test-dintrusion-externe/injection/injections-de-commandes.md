# Injections de commandes

### Basiques

```
; <CMD>
```

### Go

```
# Exemple de code Go vulnérable
    cmd := exec.Command("sh", "-c", "cat " + animal)
# Injection via Burp
    "animal":"dog | ls -l"
```
