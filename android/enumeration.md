# Enumération

## Statique

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

## Dynamique

1. Installer l'APK sur un téléphone.
2. Ouvrir un port sur le PC d'audit.
3. Lancer BurpSuite en écoute sur ce même port.
4. Ajouter un proxy sur la connexion Wi-Fi du téléphone. Le proxy correspond à l'adresse IP du PC d'audit et le port à celui ouvert.
