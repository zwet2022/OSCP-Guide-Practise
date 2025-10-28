## Structuur

### Overzicht

Bij iedere CTF (Capture The Flag) is structuur in werkwijze het belangrijkst. De volgende aandachtspunten moet ik aanhouden bij iedere CTF.

#### Aanpak

- Bij het starten van iedere CTF, map aanmaken met `/root/<naam-ctf>` en vanuit hier werken.
- Alle wordlists staan gedocumenteerd in `/usr/share/wordlists`.
- Bij het starten, altijd werken vanuit de root user -> `sudo su`.
- Documenteren van iedere CTF (op host-machine) via Visual Studio Code (markdown) met mappenstructuur `/practise/<ctf-naam>/`:
    - `recon.md` -> reconnaissance & enumeratie fase.
    - `poc.md` -> proof of concept uitwerking / exploitatie fase.
    - `access.md` -> initial access.
    - `privesc.md` -> Privilege Escalation & Lateral Movement fase.
    - `creds.txt` -> bewaringen van cleartext & hashes (wachtwoord) in format `<username>:<hash>/<wachtwoord>`. 
