---
layout:     post
title:      "My OSCP Journey"
date:       2020-03-16 00:00:00
author:     J
summary:    I Tried Harder
categories: OffSec
thumbnail:  certificate
tags:
 - OSCP
 - Exam
 - PWK
 - Offensive Security
 - OffSec
---



Disclaimer: This post is still fresh and subject to changes in the coming days



## #whoami

Just a foreword before you go on to read this entry. Everyone has different backgrounds, experiences, time constraints, personal commitments and learning capabilities. Because of this, your mileage may vary from the experiences I am about to share here, and I do not wish to give anyone false hopes or expectations going to the course and/or the exam.  You may be faster or you may be slower; who knows? But we will all get there eventually.

This section is to give you a rough baseline of who I am and what I already knew before embarking on the journey. Here I will share the story of my journey to the OSCP, and how my exam went. But due to non-disclosure, I will not disclose any information on the exam machines. 



### My job

I am currently holding a full time Cybersecurity role in the little sunny(and sometimes rainy) island of Singapore. I have been in this field for 1.5 years at the time of writing. My specialisation lies in Penetration Testing, Incident Response and Threat Hunting.



### My educational background

I graduated with a Bachelor's Degree from the University of Portsmouth studying Digital Forensics. As with many IT related courses, there was a heavy emphasis on cybersecurity in it. I have over the course of this degree created vulnerable applications for exploitation, as well as touched on assembly level debugging for Malware Forensics.



### Related activities, courses and certiffications prior to the OSCP

I currently hold the Certified Ethical Hacker (CEH) certification from the EC-Council. Approximately 6 months prior to starting my [Penetration Testing with Kali (PWK)][1] course, I was playing around on [Vulnhub][2], and [Hackthebox][3], achieving "Hacker" rank on the latter. Also, I enrolled for the [VirualHackingLabs][4] course and obtained both their Basic Completion and Advanced+ certifications.



All in all, I had exploited and rooted at least 50-60 machines prior to starting the PWK course. For those interested, I have a small writeup on my VHL experience [here][5].



---



## The PWK Course

My purchased 2 month course started somewhere in the first week of February. But for the first 2 weeks there was not much done in the labs. People knowing me in real life would know why. Worth it, I'd say ;)

I immediately scheduled my first exam attempt 1 month into the course. I didn't expect anything out of it, but just wanted to test myself and get a feel for the exam. If I failed I'd have another month of labs to practice before attempting the exam again.

The 2 weeks prior to the exam was where I really started playing in the labs, I had taken time off work to focus on preparing for the exam. I also spent about 2 entire days familiarising myself with Buffer Overflows and Windows Privilege Escalation from various guides. The latter was a major weakness for myself and most people I know.

All in all, I actually only spent about 2 weeks working on the labs.



## The Exam



Based on information publicly shared on the internet, the point values of the machines are as follows:

1. 25 (Buffer Overflow)
2. 25
3. 20
4. 20
5. 10



The highest possible total point value is *100*. To pass the exam, you need a minimum of *70* points. *5* bonus points may be awarded if you submit your lab report with your exam report submission.



The exam is gruelling and challenging, lasting a total of 23h45m. Of course, it's much easier(and cooler) to say 24h. But that's wrong either, since you are required to log into the proctoring application 15 minutes prior to the exam.

Due to some changes by Offensive Security the year prior, I was taking the new proctored version of the exam. Exam machines were also said to be updated, so there is a possibility that there are newer and possibly harder machines in there.



Tools which perform automated exploitation are not allowed during the exam. You may only use Metasploit modules(with some exceptions) or Meterpreter payloads on a single target. If you attempt to execute something using them and it fails, it is still considered usage and you may not use it anymore.



The point values I share below are under the assumption that gaining a low privilege shell is worth 1/2 the points of the machine. The actual point values of attaining these shells were never disclosed officially, so take them with a pinch of salt. Also, the points allocated do not reflect on the difficulty of the machine.



Further exam information can be found on the official site [here][6].



## My Game Plan and mindset



- Start all my scans on the target and then proceed to do the Buffer Overflow machine. By the time I was done, I should have some results to work with.

- I would scan through all 4 machines and picked any low hanging fruit that I could start with. When there were no fruits left to pick, I would move on to another machine. I did not put a specific time on how long I should spend on each machine before deciding to move on and cycle through them. I just did it by feel and not a hard timer.

- I  planned to take a short nap, but not a full 6-8 hour sleep. But if I would only do this when I feel tired or sleepy, or when I feel like it was getting hard to keep my focus.

- I planned for failure. Not that I want to fail, but with less expectations come less disappointment. The mindset of learning from failures is an important one. Just accept that this examination is known for it's difficulty and high failure rates and that there's no shame in failing it.

  

I did not prepare,  or even consider preparing the lab report, which was worth 5 points. If I somehow ended with 65 or 67.5 points, I would not use a crutch to get me that bit across the finish line. If I can do it, I can do it. If I cannot, then I will come back stronger. A bit prideful, but that's just the kind of person I am. But if you consider the possible permutations, a 65 or 67.5 score is actually **VERY** likely.



---



## The Exam Day



I had my exam scheduled to start at 7am in the morning on 7 March 2020. I was running on less than 4 hours of sleep due to the adrenaline and nerves getting to me on the night prior. 



**6.45am** - I started my setup to make sure everything was working. However, due to me using a less than ideal webcam, there were some issues verifying my identity. While the words on my identity card were readable, they weren't sharp enough, which is understandable also considering that it wasn't even sunrise yet. But we eventually got it resolved. I personally think it's great that they're taking this proctoring thing seriously; there are far too many cheaters out there giving the OSCP cert a bad name.

I actually paid about SGD$50 for this thing, the Logitech C310, which isn't a bad webcam by any means. But a tip for people who have yet to purchase or borrow a webcam, try to get one with some sort of autofocus function.



**7.20am** - The exam finally started and I received my VPN connection after the green light was given by the proctor to start.



**11.00am** - I can't really remember the exact time for this, but I got the Buffer Overflow machine. Prior to the exam I had managed to get my BOF timings down to below 15 minutes. But however I had taken over 3 hours on this due to some strange unknown reason. Of course, I was also enumerating and looking through the other boxes in the meantime.



My confidence and morale took a really big hit at this point. I had people believing in me and lots of well wishes, but I had nothing 4 hours in. Not even the BOF machine which was said to be a "free points" box.



**1.20pm** -  First low priv shell on the 20 pt machine. At this 6.5 hours into the exam and I had 35 points; half of what was needed to pass. My mistakes made during the BOF machine really caused me a lot of time.



**2.07pm** - Privilege escalation successful on that same 20 pt machine. 45 points now.



**5.26pm** - Got a low priv shell on the other 20 pt machine. 55 points!

I have worked for 10 hours straight so far. If I were to go to sleep and get some rest, I don't know for sure if there will be enough time to get that last 15 points. So I decide to go on. I have historically played video games for over 30 hours on end, so this is nothing new to me. I know what it takes to sit and focus at a computer for extended periods



**10.10pm** - Got the 10 pt machine, took me almost 5 hours but I did it. 65 points now. If I had done my lab reports I would have had the points to pass right here. But no, I had to do it the hard way. It was now 15 hours into the exam. Only less than 9 hours more to go.



**1223am** - Managed to escalate the second 20 pt one. At this point I had 75 points and had passed the exam! However, I spent time revisiting my notes and screenshots to make sure I did not miss any steps. Documentation is crucial for this examination, and they have been stories of people failing exams due to insufficient documentation, despite performing well and getting more than enough points.



**12.45am** - My girlfriend paid me a surprise visit! I had not taken a proper meal for the longest time. Not even breakfast before starting the exam. She was terribly worried about me and brought me food! I had my first short break here to eat. Yes, I did not take a single break for almost 18 hours except for when nature calls.



**1.00am** - I finished confirming that I had the screenshots I needed. I had just below 6 hours left on my exam time and was about to tell the proctors to end my exam. But I decided, hey since I'm energised from having eaten some food, let's try and tickle last 25 point box for a bit. I had visited this box countless times since the start of the exam but there was nothing at all that I could find on it. Nada. Nope. Nothing.

It was one heck of a box to get into. But hey, no harm trying anyway since there's nothing to lose except sleep at this point.  If I felt tired, I would call it a day.



**3.00am** - I got in. . I freaking got in! I "Tried Harder" and finally got a low privilege shell on this thing, 20 hours into the exam. I quickly enumerated the machine and found several possible vectors; one of which I had encountered before in a box I had previously exploited. So I spent quite a bit of time trying to replicate the exploitation from my personal past documentation. But it didn't work. Shit, a rabbit hole.



**5.45am** - 1 hour left till time is up. I managed to escalate my privileges eventually through a different vector, achieving full marks for the exam. I close my eyes and thought,.. "I f*cking  did it. 100 points in the OSCP exam, with my own abilities."



**6.15am** - I finished my final sweep to make sure all screenshots were in place, made sure my keys were properly submitted, and concluded the exam. Told the proctors to cut my VPN as I had done everything I needed. I actually managed to maintain razor sharp focus for 23 hours straight, I got all machines and finally, the suffering is over. Sort of; I still had to write my report.





---





## Takeaways and tips



1. If you're not very confident, do your lab report. As mentioned, it's extremely possible that you end up with a score where that 5 extra points will get you that OSCP certification. Otherwise, just know that failure is a chance to learn
2. Don't keep on the same machine for too long. Rotate and cycle through.
3. Understand your buffer overflows. It's alright to just be able to replicate the common steps for a basic buffer overflow, but if shit happens, this knowledge can help you to debug more effectively.
4. Manage your time properly. If you need a rest, do it. Just because I didn't doesn't mean you shouldn't either. I could hold my focus for that 24 hours. But not everybody can.
5. The report takes time! Possibly more than you might expect. Make sure you have factored that in if you're having commitments the day after your exam.
6. Acquisition rate of points is not linear. For example, if you gained 60 points in 12 hours(20pts per 4 hours), don't assume that you'll pass by spending another 2-4 hours and end up taking too long a sleep/rest. Also remember that the 25 pt buffer overflow box is known by many as a "freebie". People have also gone over 10 hours without making any progress at all, and it's common.
7. Rabbit Holes are there, as usual. If something doesn't work for too long, try something else; but take note of it. You can always try again later.
8. Keep a set of good notes. I mean stuff like command cheat sheets and stuff like that for quick reference. It does not matter if they're not very organised, just make sure you know your way around them and find what you need quickly. It's your own personal set of notes after all. Most people use OneNote, but I write mine in [Typora][7] because markdown just freaking rocks (Btw this page was written in markdown). Find something that works for you!
9. Take notes and screenshots during the exam. Lots of them. I like [cherrytree][8] for this, but OneNote works nice too. If anything even remotely looks like progress, document it immediately, lest you end up forgetting how you did it later. Copy and paste your commands, you may have to keep typing them again and again.
10. Automate stuff. Scripts are out there to help you automate enumeration. Feel free to reach out to me to ask what think about some of them, or if you need recommendations! But take note of the exam restrictions. As a rule of thumb, you may automate *enumeration* but not *exploitation*.
11. Take the exam with integrity, if you cheat you're cheating yourself. If you can't do it, Try Harder.
12. If you feel like giving up, again, Try Harder. Take a break and come back with a fresh mind.
13. I like coffee. I really do. Maybe you should have some too!



## Results and thoughts



I submitted my report in the dead of the morning at on the 9th of March just a few hours before the deadline and got the email from Offensive Security a week later confirming my passing grade and awarding me my certification.



Was I proud of my accomplishment? Yes definitely. Unlike the stories going around the internet of people cheating, asking for exam answers etc, I did not have to resort to any of that.



Did I perform up to my own expectations? Yes and no. I definitely was glad I did well, but also am very disappointed in myself  for taking too long overall. After successfully getting all 100 pts for the exam, I realised that I could have been so much faster and more efficient in my exploitation. Ideally it could have been done in about 16 hours perhaps; I shouldn't have had to stay up the entire 24 hours.s



Lastly, I would like to give thanks to everyone who gave me their support, especially my close buddies from work, my bosses, the one above for answering my prayers, and last but definitely not least, my girlfriend. Also thank you for reading this post and I hope that you too, will find success in your exploitation endeavors.



Till next time!

J



[1]: https://www.offensive-security.com/pwk-oscp/
[2]: https://www.hackthebox.eu
[3]: https:/www.vulnhub.com
[4]: https://www.virtualhackinglabs.com
[5]: https://dreamscent.github.io/virtualhackinglabs/2020/02/05/VHL-Completed/
[6]: https://support.offensive-security.com/oscp-exam-guide/
[7]: https://typora.io/
[8]: https://www.giuspen.com/cherrytree/
