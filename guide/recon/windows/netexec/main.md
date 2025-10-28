## netexec

#### Basic commands

**SMB Connection - Validating Credentials**

```
nxc smb <ip> -u <user> -p <password>
```

**SMB Connection - getting shares (folders) for a user**

```
nxc smb <ip> -u <user> -p <password> --shares
```

**SMB Connection - getting loggedon sessions if user has permission**

```
nxc smb <ip> -u <user> -p <password> --loggedon-users
```

**SMB Connection - getting loggedon sessions if user has permission**

```
nxc smb <ip> -u <user> -p <password> --loggedon-users
```

**SMB Connection - password spraying valid usernames and password without bruteforcing**

```
netexec smb <ip> -u <username-file.txt> -p <username-file.txt> --no-bruteforce | grep -v FAILURE
```

