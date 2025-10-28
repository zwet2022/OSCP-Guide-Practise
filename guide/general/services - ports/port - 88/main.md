## Port 88 / Kerberoast

### Overzicht

Kerberoast is een standaard authenticatieprotocol dat ervoor zorgt dat gebruikers van een netwerk op een veilige manier kunnen aanmelden en hun identiteit kunnen bewijzen. Wordt vaak gebruikt als tweede laag bij Active Directory.

#### Herkenning

*NMAP*
```
88/tcp   open  kerberos-sec  Microsoft Windows Kerberos (server time: 2025-10-22 10:43:53Z)
```

#### Gebruik

**Let erop dat je de tijd synced wanneer je interactie zoekt met kerberoast. Dit kan via:**

```
sudo apt install ntpsec-ntpdate
sudo sntp -s <ad-domain>
```

#### Tools

- Impacket


