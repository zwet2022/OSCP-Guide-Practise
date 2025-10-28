## Cleartext Passwords Stored

### Basic Commands

#### find "password" named files with .ini - .txt - .xml extension
```
findstr /si password *.txt
findstr /si password *.xml
findstr /si password *.ini
```

#### Find noted strings in config files

```
dir /s *pass* == *cred* == *vnc* == *.config*
```

#### Find all passwords in all files

```
findstr /spin "password" *.*
findstr /spin "password" *.*
```

#### Commonly stored password files and/or directorys
**Dir Files**
```
c:\sysprep.inf
c:\sysprep\sysprep.xml
c:\unattend.xml
%WINDIR%\Panther\Unattend\Unattended.xml
%WINDIR%\Panther\Unattended.xml

dir c:\*vnc.ini /s /b
dir c:\*ultravnc.ini /s /b 
dir c:\ /s /b | findstr /si *vnc.ini
```

#### In Registry

```
- VNC
reg query "HKCU\Software\ORL\WinVNC3\Password"

- Windows autologin
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon"

- SNMP Paramters
reg query "HKLM\SYSTEM\Current\ControlSet\Services\SNMP"

- Putty
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"

- Search for password in registry
reg query HKLM /f password /t REG_SZ /s
reg query HKCU /f password /t REG_SZ /s
```