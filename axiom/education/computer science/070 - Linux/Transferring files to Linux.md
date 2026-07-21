---
id: Transferring files to Linux
aliases:
Topic: How to transfer files to a Linux-System via an http-sever.
Related:
  - "%Linux"
Tags:
  - w
Date: 2026-04-22T19:20:00
Updated:
Source:
---
# Transferring files to Linux


https://www.youtube-nocookie.com/embed/lPk2xm7wM4M?playlist=lPk2xm7wM4M&autoplay=1&iv_load_policy=3&loop=1&start=

sudo systemctl poweroff


wenn ich files oder oderner rüber bekommen will dann auf mac nen server machen im ordner:
Auf dem Mac im Ordner:
cd /Users/DEINNAME/Ordnername
python3 -m http.server 8000
Dann auf dem Arch‑Laptop:
wget http://IP_DES_MAC:8000 -r