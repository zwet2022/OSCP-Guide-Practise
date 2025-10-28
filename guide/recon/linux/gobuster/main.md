## Gobuster rcon

##### Main commands

*Basic directory enumeration*
```
gobuster dir -u <domain> -w /usr/share/dirb/wordlists/common.txt 
```

*File enumeration*
```
gobuster dir -u <domain> -w /usr/share/dirb/wordlists/common.txt -x txt,php,html,zip
```
