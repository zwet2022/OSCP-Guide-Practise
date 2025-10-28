## User Enumeration

### Commands

##### Show current username

```
echo %USERNAME% || whoami
```

##### Show user privilege

```
whoami /priv
whoami /groups
```

##### Show all users

```
net user
whoami /all
Get-LocalUser | ft Name,Enabled,LastLogon
Get-ChildItem C:\Users -Force | select Name
```

##### Show logon requirements (Brute Force)

```
$env:usernadsc
net accounts
```

##### Show details about user

```
net user <username>
```

##### Show all local groups

```
net localgroup
```

##### Show details about a group

```
net localgroup <username>
```

##### View groups

```
net group /domain
```

##### View members of group

```
net group /domain <Group Name>
```

