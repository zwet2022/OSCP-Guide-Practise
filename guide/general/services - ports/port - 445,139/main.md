## Port 445 / 139 (SMB)

### Overzicht

Port 445 en 139 worden gebruik door windows active directory. SMB is een file sharing protocol, die automatisch gebruikt wordt bij active directory.

#### Herkenning

*Via nmap*

```
445/tcp  open  microsoft-ds?
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
```
**Te gebruiken tools**

- Met gebruikersnaam & wachtwoord:
    `smbclient` - `netexec` - `impacket`

**Waarschuwing - Brute Forcing**

Bij bruteforcing kan SMB je IP blokkeren, gebruik daarom bij password spraying no bruteforceflag.