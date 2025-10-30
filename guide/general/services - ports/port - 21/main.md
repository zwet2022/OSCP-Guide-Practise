## FTP Service

### Basics

#### Recognizion

**NMAP**

```
21/tcp open  ftp     vsftpd 3.0.5
```

#### Checklist

**Folder Structure**

See what's noted in the Folder Structure of the FTP service. Look for any:

```
- Writable/Readable folders
- Writable/Readable files
    - Backup files.
    - Emails files.
    - Credentials that are noted in any file extensions:
        <file>.mdb
        <file>.bak
        <file>.zip
        <file>.<younameit>
```

**Get everything on the file structure**

Every file needs to be downloaded, that can be downloaded.

```
[There is a command for this, gotta search that command]
```

**FTP upload rights**

```
- Look for any upload rights on the FTP service.
    - If there are rights to upload files, look where the FTP service uploads the files and in what folder of the Linux/Windows /<directory>.
```

If there are upload rights and you know where the /<directory> is placed, search for Local File Inclusion vulnerabilitys. These can run the PHP file that you have uploaded like a **shell.php**.

If there is no Local File Inclusion, the upload and/or folder structure might be in the /var/www/html directory. Try to upload an **shell.txt** file and access it via:

```
http://<ip>:<port>/shell.txt
```

if the file is there with the placed text and it can be seen. You can upload an reverse shell!

