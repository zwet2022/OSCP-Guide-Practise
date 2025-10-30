## Delivery

### Overzicht
Het overbrengen van bestanden en/of folders via een transfer systeem, waardoor het leveren van bestanden makkelijker wordt.

#### Linux naar Windows

**1. Linux opzet**

```
cd /<folder>/<where>/<file>/<is.ext>
python3 -m http.server 8080
```

**2. Windows opzet**

```
powershell -ExecutionPolicy Bypass -Command "Invoke-WebRequest -Uri http://<ip>:8088/<file.ext> -OutFile <file.ext>"
```