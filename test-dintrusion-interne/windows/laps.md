# LAPS

* Accéder au mot de passe administrateur local (nécessite les droits de lecture sur les `attributsms-Mcs-AdmPwd` et `ms-Mcs-AdmPwdExpirationTime`) :  &#x20;

```
Get-ADComputer -Filter * -Properties ms-Mcs-AdmPwd, ms-Mcs-AdmPwdExpirationTime
```
