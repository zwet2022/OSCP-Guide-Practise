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

**Summary**

Search the whole directory for cleartext passwords in files.

*See /cleartextPasswordFinding for the basic commands*

#### Services only available from inside

**Summary**

See what services are running and what you can use.

*See /activeServiceInside for the basic steps to take*

#### Kernel Exploits

**Summary**

Should be the last resource we go to when we dont find anything

*See /kernelExploits for the basic steps to take*

#### Scheduled Tasks

**Summary**

See what tasks are running. If task is run by administrator but path can be edited by you as user, than might be vuln.

*See /scheduledTasks for the basic steps to take*

#### UPNP Service Binary Overwrite

**Summary**

See if upnp service binary can be changed and replaced with our malicious.exe file.

*See /upnpService for the basic steps to take* 

#### Weak Service Permissions

**Summary**

See if you can find weak services with overwritable permissions (restart).

*See /weakServicePermission for the basic steps to take* 

#### Unquoted Service Paths

**Summary**

See if there are services that are ran as administrator, but we can change for our malicious exe file

*See /unquotedServicePaths for the basics steps to take*

#### Vulnerable Drivers

**Summary**

See if there are drivers we can exploit

*See /vulnerableDrivers for the basics steps to take*

#### AlwaysInstallElevated

**Summary**

See if the exploit AlwaysInstallElevated is installed

- if so?
    ```
    reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated
    reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated
    ```

    - http://toshellandback.com/2015/11/24/ms-priv-esc/

#### Group Policy Preference

**Summary**

See if the machine belongs to a domain and your user has access to `System Volume Information`, because there might be some sensitive files there!

*See /groupPolicyPreference for the basics steps to take*

#### Escalate to SYSTEM from Administrator

**Summary**

Steps to take to escalate from Administrator to System shell.

*See /escalateAdminToSystem for the basics steps to take*