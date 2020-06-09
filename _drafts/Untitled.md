---
layout:     post
title:      "Exploit Development Setup"
date:       2020-06-03 00:00:00
author:     J
summary:    Oh
categories: Guides
thumbnail:  thumbs-up
tags:
 - OSCE
 - CTP
---





WSL



Install Kali





```bash
sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
```



kaliWSLver.png



~~~bash
sudo apt-get install python python3-pip python3-venv build-essential python3 python3-dev git libssl-dev libffi-dev build-essential

cat etc/os-release


python3 -m pip install --upgrade pip
python3 -m pip install --upgrade pwntools

cd ~ && python3 -m venv exploitdev

python3 -m pip install boofuzz


source ~/exploitdev/env/bin/activate


sudo python3 -m pip install --upgrade pip
sudo python3 -m pip install --upgrade pwntools


sudo apt-get install metasploit-framework
~~~



>
>
>  WARNING: The script chardetect is installed in '/home/kali/.local/bin' which is not on PATH.
>  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
>  WARNING: The script pygmentize is installed in '/home/kali/.local/bin' which is not on PATH.
>  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
>  WARNING: The script mako-render is installed in '/home/kali/.local/bin' which is not on PATH.
>  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
>  WARNING: The scripts asm, checksec, common, constgrep, cyclic, debug, disablenx, disasm, elfdiff, elfpatch, errno, hex, main, phd, pwn, pwnstrip, scramble, shellcraft, template, unhex and update are installed in '/home/kali/.local/bin' which is not on PATH.
>  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.

pwnwarning.png



https://boofuzz.readthedocs.io/en/stable/user/install.html

http://docs.pwntools.com/en/stable/install.html



VS code



terminal > new terminal



vscselectshell.png



vscselectshell2.png





vscselectshell3.png



WSL Bash



install python



install boofuzz



install pwn





extra:

defenderexclusions.png