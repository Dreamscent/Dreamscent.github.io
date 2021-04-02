---
layout:     post
title:      "Certified Red Team Operator Course Review"
date:       2021-04-01 23:23:23
author:     J
summary:    Well that was fun
categories: Active Directory
thumbnail:  graduation-cap
tags:
 - Red Team
 - Zero-Point
 - Covenant
---





DISCLAIMER: This is still a draft and is subject to changes in the coming days



## An Introduction



As some may know, I recently completed the **Certified Red Team Operator** course by [Zero-Point Security][1]. This is my first foray into the Active Directory exploitation realm and what an experience it has been.



![Badge](/images/CRTO/badge.png)



The [Certified Red Team Operator][1] is a fairly new course by Daniel "RastaMouse" Duggan. the same person who created the monster challenge that is Rastalabs. If you have done the OSCP or similar certifications, you may also know him as the author of the Windows enumeration tools *Sherlock* and *Watson*.



It is a fairly intensive course which starts at a beginner-friendly level, then gradually increasing in difficulty. By the end of the course, I'd say  anyone who has completed the course to be of an intermediate level. I was exposed to a full and realistic active directory environment spanning multiple domains, which is designed for practicing and performing each and every attack type taught in the course.



According to their website, Red Team Ops course is split into the following modules:

- Introduction to red teaming
- External Reconnaissance
- Initial Compromise
- Host Reconnaissance
- Persistence
- Local Privilege Escalation
- Domain Reconnaissance
- Credentials & User Impersonation
- Lateral Movement
- Session Passing
- SOCKS Proxies
- Reverse Port Forwards
- DPAPI
- Kerberos Abuse
- Group Policy Abuse
- MS SQL Server Abuse
- Domain Dominance
- Domain & Forest Trusts
- Bypassing Defences
- Complete Mission
- Wrap Up & Post-Engagement



As you can see, there is a fairly wide range of topics that it will cover, and by the end of the course, the participant will definitely be familiar with all of them. The reason why will be explained in the next section. This is also the first (and only?) course designed around the [Covenant][3] Command & Control (C2) Server. For those who already are in red teams or are lucky enough to get hold of a license, it also teaches the use of Cobalt Strike.



By the end of the course, you will have to take a 48 hour exam, and collect "flags" along the way. At the time of writing, the passing criteria is 3 out of 4 flags. The great thing is that results are almost immediate, and that you do not have to write a report which is great!



Some companies put emphasis on a quality report and won't give you a passing grade if it's subpar, which adds value to a certification. But on the other hand, some are willing to accept garbage, which is a waste of everyone's time.



In addition, Zero-Point Security is a [CREST member][4] company, which means that when this certification gains traction, it's certification may hold some additional value in countries where CREST has a large presence such as the UK, Hong Kong, and Singapore.





## The course structure



When the course was first launched, there were two pathways one can take to attain the CRTO.



1. Complete the course, and pass the exam
2. Attain the OSCP, then take and pass the exam



However, during the recent months, the second option was removed. And I feel this is for the better and adds more value to the certification.



Why? Because to mark a course module as complete, you have to perform and exploit the vulnerability/misconfiguration within the labs to attain a flag. This ensures that the student knows how each attack is performed. As you can see, there are way more than 10 modules in the syllabus above. 



Let's put this into perspective. For example, imagine there is a competitor **ABC**. They give you some training materials with 10 modules, and an exam that tests only 3-5 of the attacks. A student can theoretically not understand half the things taught at all, yet still be able to pass the exam and be certified. This would make me question the capabilities of someone with **ABC**'s cert. That's why I think the removal of the second option was a good move that adds more value to the certification.





The course uses [badgr][5] pathways, where you have to complete modules and submit the flags to attain a badge. Some badges may require multiple tasks with different attack types to be attained.



![Badgr](/images/CRTO/badgr.png)



You may purchase the labs in 30, 60, or 90 day denominations, and it comes with an exam attempt. As of time of writing, lab time extensions also give an additional exam attempt.



For myself I purchased 30 days back in August 2020(6 months ago), but was unable to finish the labs in time. I later purchased another 2x 15 day extensions, because my day job started to require quite a lot of overtime.



For most, I believe 60 days would be a comfortable timeframe to complete the course. But if you have a ton of free time, or have prior experience, go for the 30 day package.



## The competitors



This might be why you're here isn't it? You may be interested in taking up a Red Teaming oriented course, but are considering between several options, and hence are googling around for reviews to decide which you should take. Hopefully this section will help a little.



Disclaimer, I may have some insights on the following courses and did some research, but have not taken the following courses (or not yet anyway), so take the following with a pinch of salt. 




### Pentesteracademy - Certified Red Ream Professional (CRTO)



This is a beginner certification which introduces the student to the world of AD exploitation. It covers most of the basic topics and has a fairly heavy emphasis on the command line and powershell. It however does not teach you how to use a Command & Control (C2) server.



[Link][6]



### Pentesteracademy - Certified Red Ream Expert (CRTE)



It's a sequal to the above CRTP, expanding on the concepts with a few more techniques, and is more of an intermediate level course which requires some prior AD exploitation knowledge.



[Link][7]



### eLearnSecurity - Certified Penetration Tester eXtreme (eCPTXx2)



This is a course which I have purchased  but have yet to start working on. Based on the course materials, this mostly overlaps with the CRTO's syllabus, but  goes a bit further. According to [this review][https://github.com/ryan412/ADLabsReview] written by a guy who has both CRTO and PTX(v1), he rates them both as *intermediate* in terms of difficulty. But I would definitely say the PTX is tougher.



[Link][8]



###  Offensive Security - Experienced Penetration Tester (OSEP)



This is the grand daddy, the only certification course rated as *hard* based on the above review(gosh he has done everything). On top of active directory exploitation, this is VERY defense evasion heavy, which is great because in a real Red Teaming engagement, you must be able to perform your activities without being caught by various blue team tools and software.



[Link][9]



### Pentesteracademy - Certified Enterprise Security Specialist (PACES)



I have very limited information on this one, but it seems to be of a high difficulty as well.



[Link][10]



## The good and bad



**The good:**

- Dedicated friendly and active slack channel where Daniel the man himself is there to assist

- lab connection is fast and stable, load balancing

- lifetime access and to the latest course updates

- certification does not expire



**The not-so-good:**

- Does not come with a pdf or physical certificate, just a badge. Zero-Point has a really nice logo so a certificate with would look pretty neat in a CV.

- Covenant is still under development, where there are some instability issues and bugs, and it can cause some frustration here and there.





## The Exam



I took the exam at the end of March. It was noteworthy that I had not finished the labs by this point of time, and had a few things I haven't learnt.



At the start time, my VPN connection files were sent to me via email promptly and my connection was made. All 4 flags were actually fairly straightforward with no monkey business. Either you knew your stuff or you don't.



In less than a few hours, I had the first flag under my belt. However, due to some strange issue, I was stuck at a particular machine for about 24 hours(including sleep and meals of course). I had consulted the course materials, the tool documentation, various reputable guides and blogs on the topic, but the commands used just could not work. In the end, I could only achieve it via some other weird way. It was a very straightforward task, but till today, I still don't know if there was an issue with the exam machine, my tool, or just me being bad at what I do. Perhaps I will never know.




Once I got through, the second and third flags fell rather quickly, allowing me to get my passing score by the 30 or so hour mark(can't remember the exact time though). By then, I was tired and fairly pissed at the issues I was having(I had to reset Covenant 3 times during my exam in total because everything became unresponsive, and start from scratch to regain all my lost Grunts(which is sort of like a shell on the targets)). I knew where the last flag was, and how to get it, but Covenant decided to crap out on me again, so I called it a day.



All in all, my total exam time was definitely much slower than most(I read that the average is below 24 hours comfortably). If not for the issues I faced, I most likely would have done it in less than 6-8 hours. Perhaps even faster if I actually completed the labs prior to the exam, as there were some things I had to learn on the spot.



Of course, passing the exam alone did not equate to the CRTO certification, so I went back to the labs and spent the next day or so finishing up what I was missing.



## Final words

Overall, I think this is by far one of the best courses I have ever done, as well as the most fun(and sometimes frustrating). It's cost may seem high at first compared to the offerings from Pentesteracademy, but don't forget that the learning and amount of content provided here is akin to both CRTP and CRTE combined(at least from what I see in the syllabus).



I would definitely recommend this to anyone who wants to try to start dipping their toes in to the world of Red Teaming and Active Directory exploitation. If you have complete the labs, you definitely would have more than enough knowledge and skills to pass exam. If anything, the labs are harder than the exam itself!



If you have any questions, feel free to connect and reach out to me on LinkedIn!



J





[1]: https://www.zeropointsecurity.co.uk/
[2]: https://www.zeropointsecurity.co.uk/red-team-ops
[3]: https://github.com/cobbr/Covenant
[4]: https://service-selection-platform.crest-approved.org/member_companies/zero-point-security-ltd/
[5]:  https://eu.badgr.com/public/pathway/5e84547c7aa1db408520004a
[6]: https://www.pentesteracademy.com/activedirectorylab
[7]: https://www.pentesteracademy.com/redteamlab
[8]: https://elearnsecurity.com/product/ecptx-certification/

[9]: https://www.offensive-security.com/pen300-osep/

[10]: https://www.pentesteracademy.com/gcb











