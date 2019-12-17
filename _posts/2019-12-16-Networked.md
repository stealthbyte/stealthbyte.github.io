---
layout: post
title: Networked
description: HackTheBox - Easy Linux Machine
image: assets/images/networked.jpg
---
 
This machine has a simple website running that has a vulnerable file upload capability. Performing some web enumeration found a backup archive that showed exactly what type of php files are running with the source code. After reviewing these we find a upload.php that looks interesting and we have to bypass the checks to upload a php web shell. Once on target we have to abuse a cronjob that runs for a specific user to gain access to his account, then abuse sudo permission for that user and a file he is able to modify to acheive RCE as `root`.
 

## Summary 
- Found /upload.php running on port 80
- Leveraged this to get RCE on machine
- Escalated to user from apache due to vulnerable cronjob running
- Once regular user executed : `sudo -l` and found interesting file to execute
- Abused this file to gain `root`

## PortScan
```

nmap -sC -sV -p- <Target IP>

-- Ports Found!

```

## Port 80 Exposed Running 
```
Snippet of Page
```

### Ran gobuster and found interesting stuff.
```
# Need to download this first
git clone https://github.com/danielmiessler/SecLists.git

# From snowscan.io
gobuster -w raft-large-words-lowercase.txt -t 25 -u http://<target> -s 200,204,301,302,307,401
```

### Looking for foothold with `interesting folder/`


