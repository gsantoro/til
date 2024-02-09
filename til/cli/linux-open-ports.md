---
title: linux-open-ports
draft: true
tags: 

---
# Linux - open ports
List the ports open and listening for connections
```
sudo lsof -i -P -n | grep LISTEN
```