# Guide & Practise - *Road to OSCP*

## Summary

I began practising for the OSCP certification in mid 2025. To bridge the gap between bug bounty hunting and OSCP-level penetration testing, i’ll be practicing on TryHackMe and HackTheBox. This repository documents my journey, showcasing both my practical exercises and the notes I’ve developed along the way. 

*Kind of like my own little portfolio, sharing the knowledge i learn to help others!*

## Why am i doing this?

I want to know how much knowledge i can gather, from creating my own labs or getting hands on experience from free ones!

## How it works

When i'm practising with selfmade labs or tryhackme/hackthebox machines, i will be taking notes in the `/guide` folder. This folder will have 4 main fases and 1 if i get stuck ;) 

In the practise folder, you can find the walkthrough of the CTF (Capture The Flag) i have taken notes from.

**Further down you can find the whole structure of the folder**

The `/Guide` folder has the following **methodology** steps:
```
    - Recon used to note Tools i can use to start my Information Gathering fase.
    
    - Post-exploitation used to remind myself of exploitation steps to get RCE, LFI, SSTI, XSS or SSRF (findable in /linux, gonna make it general so /windows machines canbe exploited to) and exploitation steps for Active Directory (Still learning!!).
    
    - Initial-access reminding myself to get a stabalized shell and progressing that further.
    
    - Priv-esc for notes to give me a general idea of what to check for Linux and Windows machines. Soon will be adding techniques for Active Directory
```

### Folder Structure

```
------
/Guide
    --------
    /general
    ------------
        /services - ports
    ------------
    /initial-access
    ------------
        /shells
    ------------
    /post-exploitation
    ------------
        /linux
        -----------
            /web-techniques 
        -----------
        /windows
    ------------
    /priv-esc
    ------------
        /linux
        /windows
    ------------
    /recon
    ------------
        /linux
        -----------
            /[Tools (Basics)]
        -----------    
        /windows
    ------------
    --------
------

---------
/Practise
    ------
    /linux
    /windows
    ------------
        /Active Directory
        /Windows Box
    ------------
    ------
---------
```

