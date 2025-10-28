## Sudo

### Overzicht

Sudo heeft verschillende werkingen, waarvan een root uitvoering en andere commando's. In dit overzicht zie je hoe je recon en exploits kunt uitvoeren via het sudo commando.

#### Sudo -l

**Invoer:**

```
sudo -l
```
**Response: (Voorbeeld)**

```
Matching Defaults entries for asterisk on ip-10-10-249-94:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

Runas and Command-specific defaults for asterisk:
    Defaults!/usr/bin/fail2ban-client !requiretty

User asterisk may run the following commands on ip-10-10-249-94:
    (ALL) NOPASSWD: /usr/bin/fail2ban-client
```

##### Proof of concept

- Je komt in shell
- Gebruiker typt `sudo -l` om te zien wat hij mag.
- Gebruiker mag een library uitvoeren met sudo rechten.
- Gebruiker maakt commando aan in fail2ban-client service, met een reverse shell of andere commando's om root te worden.
- Gebruiker runt deze commando met `sudo` en wordt root user. 


