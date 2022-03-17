# Enumération

### strings

Utiliser la commande `strings` sur un APK peut permettre de récupérer des informations sensibles.

```
strings <FILE.APK>
```

### MOBSF

MOBSF est un _framework_ qui permet de faire une analyse statique d'un APK. Pour l'utiliser, il suffit de l'installer et de se rendre sur l'interface web (`http://127.0.0.1:8000`) pour y uploader l'APK.

[https://github.com/MobSF/Mobile-Security-Framework-MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF)

### apktool

Cet outil permet de décompiler un APK.

```
apktool d <FILE.APK>
```
