## recon

#### NMAP

```
nmap -sC -sV ua.thm
```

```
Starting Nmap 7.95 ( https://nmap.org ) at 2025-10-17 06:04 EDT
Nmap scan report for ua.thm (10.10.247.224)
Host is up (0.086s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 d9:f0:6f:0e:12:42:59:3b:b3:26:d5:4f:1e:7a:ce:ac (RSA)
|   256 63:0a:e5:79:67:0b:68:04:71:2e:0a:c1:9e:8f:a0:38 (ECDSA)
|_  256 db:d3:0b:aa:9a:1b:fe:a8:13:25:59:70:2e:cd:5e:14 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: U.A. High School
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 10.55 seconds
```

#### dirbuster

```
dirb http://ua.thm/
```

#### Handmatige recon

- Path has /assets/index.php
- With parameter fuzzing got a hit on cmd=ls
    - Returns a reverse shell parameter Command execution