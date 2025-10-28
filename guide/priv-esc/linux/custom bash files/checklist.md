## Custom Bash File

### Overzicht

Heb je sudo (NOPASSWD) privileges over bepaalde bash script?

#### Stappen

- Kijk naar de syntax in de bash file.
- Zoeken naar `$variable` waar in getypt mag worden:
    `read -p "Enter 'date' to timestamp the file: " variable`
- Word geexecute in volgende context?
    - `$error 2>/dev/null` / `exec $error` om de een of andere manier.

- Typ `/bin/bash` in de input en je word vanzelf de user met sudo privs. 