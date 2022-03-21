# Cassage d'empreinte/MDP

### LM <a href="#9330" id="9330"></a>

Présent dans la base SAM ou NTDS.

**Exemple :** `299BD128C1101FD6`

```
john --format=lm hash.txt
hashcat -m 3000 -a 3 hash.txt
```

### NTHash (A.K.A. NTLM) <a href="#b5a5" id="b5a5"></a>

Présent dans la base SAM ou NTDS

**Exemple :** `B4B9B02E6F09A9BD760F388B67351E2B`

```
john --format=nt hash.txt
hashcat -m 1000 -a 3 hash.txt
```

### NTLMv1 (A.K.A. Net-NTLMv1) <a href="#1070" id="1070"></a>

Obtenu avec Responder.

**Exemple :** `u4-netntlm::kNS:338d08f8e26de93300000000000000000000000000000000:9526fb8c23a90751cdd619b6cea564742e1e4bf33006ba41:cb8086049ec4736c`

```
john --format=netntlm hash.txt
hashcat -m 5500 -a 3 hash.txt
```

### NTLMv2 (A.K.A. Net-NTLMv2) <a href="#4fef" id="4fef"></a>

Obtenu avec Responder.

**Exemple :** `admin::N46iSNekpT:08ca45b7d7ea58ee:88dcbe4446168966a153a0064958dac6:5c7830315c7830310000000000000b45c67103d07d7b95acd12ffa11230e0000000052920b85f78d013c31cdb3b92f5d765c783030`

```
john --format=netntlmv2 hash.txt
hashcat -m 5600 -a 3 hash.txt
```

### Clé GPG&#x20;

```
gpg2john key.priv > hash.john
john --wordlist=<FILE> hash.john
```

### Clé SSH

```
ssh2john.py id_rsa > hash.john
john --wordlist=<FILE> hash.john
```

### Mot de passe Linux (/etc/shadows)

**Exemple :** `$6$xyz$/pdZy4hazXmqu1t0TACitLlKZPD4bFyRUw6ycXiOTdf4kcnkmpgmtg9zUpEE8rG9KtOWwX7kp1Gl96NCGbDk60`

```
john --wordlist=<FILE> hash.john
```

### Fichier Keepass

```
keepass2john <FILE.kdbx>
```

### Masques

Il est possible d'utiliser des masques pour définir des _pattern_ de mot de passe lors d'une tentative de cassage de _hash_ :&#x20;

```
# Ajouter deux chiffres au mot PASSWORD
john --mask=PASWORD?d?d <FILE.TXT>

#
?d = chiffre
?u = majuscule
?l = minuscule
?s = caractère spécial
?a = tous les caractères
[x-y] = un intervalle entre x et y 
```

### Faire un dictionnaire personnalisé

Mettre quelques mot dans un fichier.

```
hashcat --force <WORD-FILE.TXT> -r rules.rule --stdout > <DICO.TXT>
```

La règle utilisée : [https://github.com/NotSoSecure/password\_cracking\_rules/](https://github.com/NotSoSecure/password\_cracking\_rules/blob/master/OneRuleToRuleThemAll.rule)

_**Note :** Appliquer une règle L33T en plus peut s'avérer utile. (penser aux majuscule également)_

```
f = open("dico.txt", "r")
s = ""
for pwd in f:
    print(pwd.replace('a','4').replace('e','3').replace('s','5').replace('o','0'))
```

#### TIPS :&#x20;

* Il est possible de voir les mots de passe déjà cassés grâce à l'outil `john` avec l'option `--show`.
