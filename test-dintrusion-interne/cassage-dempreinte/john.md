# john

### LM <a href="#9330" id="9330"></a>

Présent dans la base SAM ou NTDS.

**Exemple :** `299BD128C1101FD6`

```
john --format=lm hash.txt
```

### NTHash (A.K.A. NTLM) <a href="#b5a5" id="b5a5"></a>

Présent dans la base SAM ou NTDS.

**Exemple :** `B4B9B02E6F09A9BD760F388B67351E2B`

```
john --format=nt hash.txt
```

### NTLMv1 (A.K.A. Net-NTLMv1) <a href="#1070" id="1070"></a>

Obtenu avec Responder.

**Exemple :** `u4-netntlm::kNS:338d08f8e26de93300000000000000000000000000000000:9526fb8c23a90751cdd619b6cea564742e1e4bf33006ba41:cb8086049ec4736c`

```
john --format=netntlm hash.txt
```

### NTLMv2 (A.K.A. Net-NTLMv2) <a href="#4fef" id="4fef"></a>

Obtenu avec Responder.

**Exemple :** `admin::N46iSNekpT:08ca45b7d7ea58ee:88dcbe4446168966a153a0064958dac6:5c7830315c7830310000000000000b45c67103d07d7b95acd12ffa11230e0000000052920b85f78d013c31cdb3b92f5d765c783030`

```
john --format=netntlmv2 hash.txt
```

### Clé GPG&#x20;

```
gpg2john key.priv > hash.john
john --wordlist=<FILE> hash.john
```
