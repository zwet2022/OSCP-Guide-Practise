## Escalate to SYSTEM from Administrator

### Basic Steps to take

If you have a GUI with a user that is included in Administrators group you first need to open up ``cmd.exe`` for the administrator. If you open up the cmd that is in Accessories it will be opened up as a normal user. And if you rightclick and do ``Run as Administrator`` you might need to know the Administrators password. Which you might not know. So instead you open up the cmd from ``c:\windows\system32\cmd.exe``. This will give you a cmd with Administrators rights.

From here we want to become SYSTEM user. To do this we run:

**First we check what time it is on the local machine:**

```
time

- Now we set the time we want the system CMD to start. Probably one minuter after the time.
at 01:23 /interactive cmd.exe
```

And then the cmd with SYSTEM privs pops up.

#### Vista and Newer

You first need to upload PsExec.exe and then you run:

```
psexec -i -s cmd.exe
```

#### Kitrap

On some machines the ``at 20:20`` trick does not work. It never works on Windows 2003 for example. Instead you can use Kitrap. Upload both files and execute ``vdmaillowed.exe``. I think it only works with GUI.

```
vdmallowed.exe
vdmexploit.dll
```