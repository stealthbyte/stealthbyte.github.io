---
layout: post
title: Networked
description: HackTheBox - Easy Linux Machine
image: assets/images/networked.jpg
---

## Summary 
- Found x running on x
- Leveraged this to get RCE on machine
- Escalated using X
- Owned

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


