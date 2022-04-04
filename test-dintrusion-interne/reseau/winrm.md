# WinRM

* Réaliser une connexion distante :&#x20;

```
# Avec un identifiant et un mot de passe
evil-winrm -u "<USER>" -p "<PASSWORD" -i <IP>

# Avec un certificat et une clé privée
evil-winrm -i <IP> -u random -p random --ssl --pub-key <FILE.crt> --priv-key <FILE-decrypted.key>
```

**Outil :** [https://github.com/Hackplayers/evil-winrm](https://github.com/Hackplayers/evil-winrm)
