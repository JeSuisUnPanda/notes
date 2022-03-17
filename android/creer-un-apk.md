# Créer un APK

Pour créer un APK valide, deux étapes sont obligatoires. La première consiste à "construire" l'APK et la seconde à le signer.

```
# Construire l'APK
apktool b <APK-DIRECTORY> -o <FILE.APK>

# Signer l'APK
keytool -genkey -v -keystore my-release-key.keystore -alias alias_panda -keyalg RSA -keysize 2048 -validity 10000
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore <FILE.APK> alias_panda
```
