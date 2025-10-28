## Privilege Escalation

### Checklist

#### User Enum

**Summary**

get all information about the current user you are.

*See /userEnum for the basic commands*

#### Network Enum

**Summary**
Get all information about the firewall & network.

*See /firewallEnum for the basic commands*

#### Vulnerability Patch History Enum

**Summary**

Get all information about the patch history (vulnerabilitys) of the users machine.

*See /updateHistoryEnum for the basic commands*

#### Cleartext Password

Search the whole directory for cleartext passwords in files.

*See /cleartextPasswordFinding for the basic commands*

#### Services only available from inside

See what services are running and what you can use.

*See /activeServiceInside for the basic steps to take*

#### Kernel Exploits

Should be the last resource we go to when we dont find anything

*See /kernelExploits for the basic steps to take*

#### Scheduled Tasks

See what tasks are running. If task is run by administrator but path can be edited by you as user, than might be vuln.

*See /scheduledTasks for the basic steps to take*

#### UPNP Service Binary Overwrite

See if upnp service binary can be changed and replaced with our malicious.exe file.

*See /upnpService for the basic steps to take* 

#### Weak Service Permissions

See if you can find weak services with overwritable permissions (restart).

*See /weakServicePermission for the basic steps to take* 

**// proceed further with unquoted service paths**
https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_windows.html