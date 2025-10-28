## Old Zipped Files

### Overzicht

Voor het geval je een bestand.old.zip vindt met een wachtwoord erop.

#### stappenplan

##### 1. Herkennen of wachtwoord erop zit:

```
unzip <bestand>.old.zip
```

*response*

```
password for file:
```

##### 2. Kraken met john

*Van shell afhalen door:*

```
python3 -m http.server 8088
```

*Op eigen terminal verder:*

```
wget http://<victim-machine-ip>/<zipfile>
```

```
zip2john <zipfile> > hashed_zip
```

```
john hashed_zip --wordlist=/usr/share/wordlists/rockyou.txt
john hashed_zip --show
```

