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

**Exploitation**

Om SMB te kunnen gebruiken, dien je meestal een combo van `gebruikernaam:wachtwoord` te weten.

Soms kan het zo zijn dat SMB het toelaat dat de combinatie word toegestaan:

```
Gebruikersnaam: Guest
Wachtwoord:

/

Gebruikersnaam: anonymous
wachtwoord: anonymous
```

**Recon**

Indien dit werkt en de gebruikersnaam en/of wachtwoord gevonden is, kunnen de files van de Server worden gehaald. Zoek naar de shares die toegestaan zijn voor de gebruiker met bijv: `netexec` of `smbclient`.

Het hoofddoel van SMB is om bestanden zoals te behouden:

```
- backups
- credentials
- hashes
```

**Hiervan moet alles gedownload worden om het lokaal te examineren**

hieruit kunnen de volgende resultaten komen:

```
- password protected ZIP bestanden
- hashes/credentials verwerkt in bestanden zoals:
    <file>.bak
    <file>.zip
    <file>.mdb
    <file>.sql
    <go on further you know>
```

Het idee is om deze credentials allemaal uit te testen op **eerst ftp**, deze cyclus van boven naar beneden te herhalen en daarna de credentials te noteren.

**Deze gevonden credentials kunnen herbruikt worden voor het zelfde doeleind bij andere services zoals:**

```
- telnet
- ssh
- http
- <noemermeer>
```

**Tip: Crack iedere hash, sla elk cleartext wachtwoord op en herbruik het bij privilege escalation, exploitation van andere services.**

**Tip: herken de gebruikersnamen uit het onderzoek, zodat je het kan gebruiken wanneer je dit ziet.**



