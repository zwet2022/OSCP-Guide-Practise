## Checklist

### Hostname

```
hostname
```

### Kernel Info

```
uname -a
```

### Processes

```
cat /proc/version
```

### System Info

```
cat /etc/issue
```

### Environment Variables

```
env
```

### All commands that can be run by sudo (root)

```
sudo -l
```

### General overview of users privilege level

```
id
```

### Overview of users without the formatting

```
cat /etc/passwd | cut -d ":" -f 1
```

### Find commands

#### Find all files with SUID bits in it

```
find / -type f -perm -04000 -ls 2>/dev/null
```

#### Find file with certain name

```
find . -name <file_name.extension>
```

#### Find directory with certain name

```
find / -type d -name <dirname>
```

#### Find all files with executable, writable and readable by all users 

```
find / -type f -perm 0777
```

#### Find all files for user under directory

```
find /<dirname> -user <username>
```

#### Find writable folders

```
find / -writable -type d 2>/dev/null
```

### Get capabilites of a user

```
getcap -r / 2>/dev/null
```

### Get all cronjobs from crontab

```
cat /etc/crontab
```

### Get $PATH thats for our user

```
echo $PATH
```

### Get list of all NSF (Network File Sharing) configurations

```
cat /etc/exports
```





