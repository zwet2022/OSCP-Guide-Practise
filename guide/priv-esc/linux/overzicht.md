## Linux Privelege Escalation

### starters - Recon

**Informatie over gebruikersrechten**

*Zie /sudo/overzicht.md voor proof of concept*
```
sudo -l
```
**Informatie over files & binarys die met root privileges uitgevoerd kunnen worden door ons**

```
find / -perm -u=s -type f 2>/dev/null
```

- Het resultaat wat hier uit komt, kunnen we checken met `ls -la /dir/to/<binary>`
    - Komt hier iets uit met volgende structuur: `-rwsr-sr-x`
        - Ja? Dan kunnen we er iets mee. Meer onderzoek doen.

**Informatie over runnende services die aanstaan**

```
service --status-all | grep '+'
```


### Intermediate - Recon


### Geavanceerde - Recon
