## recon

### overzicht

Om een begin overzicht te krijgen van iedere aanvalsvectoren, is het nodig om een overzicht te krijgen van alle services, ports en protocollen waar de machine gebruik van maakt. In dit overzicht staan de basis commando's voor het verkrijgen van deze informatie via nmap.

#### Basis Commando's 

**Normaal overzicht**

```
nmap -sC -sV <ip/hostname> 
```

**Normaal overzicht met file output**

```
nmap -sC -sV <ip/hostname> > nmap_scan.txt
```

#### Rustscan

**RustScan als tweede voor nmap niet helpt**

```
https://github.com/bee-san/RustScan.git
```

```
rustscan <domain> --no-nmap --ulimit 10000
```




