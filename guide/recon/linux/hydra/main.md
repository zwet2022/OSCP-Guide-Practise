## Hydra

#### Basic Commands

*Basic Authentication over GET request*

```
hydra -l <username> -P /usr/share/wordlists/rockyou.txt <ip> -s <port> http-get  
```