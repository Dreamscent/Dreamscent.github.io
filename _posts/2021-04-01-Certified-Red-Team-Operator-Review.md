---
layout:     post
title:      "Red Team Ops Course Review"
date:       2021-04-02 23:23:23
author:     J
summary:    Well that was fun
categories: RedTeaming
thumbnail:  graduation-cap
tags:
 - Red Team
 - Zero-Point
 - Covenant
 - Active Directory
---



## An Introduction



As some may know, I recently completed the **Red Team Ops** course by [Zero-Point Security][1]. This is my first foray into the Active Directory exploitation realm and what an experience it has been.



![Badge](/images/CRTO/badge.png)



The [Red Team Ops][1] is a fairly new course by Daniel "RastaMouse" Duggan, released somewhere in the second half of 2020. the same person who created the monster challenge that is Rastalabs. If you have done the OSCP or similar certifications, you may also know him as the author of the Windows enumeration tools *Sherlock* and *Watson*. Completion of the course and passing the exam earns you the **Certified Red Team Operator (CRTO)** badge.



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



At the end of the course, you will have to take a 48 hour exam, and collect "flags" along the way. At the time of writing, the passing criteria is 3 out of 4 flags. The great thing is that results are almost immediate, and that you do not have to write a report. Awesome!



In addition, Zero-Point Security is a [CREST training partner][4] company, which means that when this certification gains traction, HOPEFULLY it's certification may hold some additional value in countries where CREST has a large presence such as the UK, Hong Kong, and Singapore.  As a lifelong student, I'm not a big fan of expiring certifications, so I'd be much more willing to spend my own hard earned money on attaining the CRTO, eCPTX or OSEP over something like the CCT (infra), CCSAS(simulated attack specialist), or whatever SANS has to offer in this domain.





## Red Team Ops



When the course was first launched, there were two pathways one can take to attain the CRTO.



1. Complete the course,AND pass the exam (just passing the exam without clearing the labs would not work)
2. Attain the OSCP, then take and pass the exam (discontinued)



However, during the recent months, the second option was removed. And I feel this is for the better and adds more value to the certification.



Why? Because to mark a course module as complete, you have to perform and exploit the vulnerability/misconfiguration within the labs to attain a flag. This ensures that the student actually knows how each attack is performed, and is able to successfully replicate it. 



Let's put this into perspective. For example, imagine there is a competitor **ABC**. They give you some training materials with 10 modules, each teaching a type of AD attack, and an exam that tests only 3-5 of the attacks. A student can theoretically not understand half the things taught at all, yet still be able to pass the exam and be certified. This would make me question the capabilities of someone with **ABC**'s cert. That's why I think the removal of the second option was a good move that adds more credibility to the holder of the CRTO.



The course uses [badgr][5] pathways, where you have to complete modules and submit the flags to attain a badge. Some badges may require multiple tasks with different attack types to be attained.



![Badgr](/images/CRTO/badgr.png)



You may purchase the labs in 30, 60, or 90 day durations, and it comes with an exam attempt. As of time of writing, lab time extensions also give an additional exam attempt. In the first few months of the course, it was difficult to even purchase the course due to it being always fully booked; I had to camp the purchase page for several days to be able to snag a spot in this course. Thankfully lab capacity has been increased over time, so it's quite a lot easier to enrol in RTO now.



For myself I purchased 30 days back in August 2020(6 months ago), but was unable to finish the labs in time. I later purchased another two 15 day extensions in order to finish the labs; one towards the year end of 2020 and one in March 2021 because I had quite some work piled up on my day job.



The course materials are web-based instead of a downloadable pdf, and is constantly being updated. During the 6 or so months since I first purchased the course, the course materials had been updated several times! So by enrolling into this, you know that your materials will not become obselete over time. In comparison, some competitors release a v2, v3 etc of their course every other year and force you to pay if you want the updated stuff.



As I have also mentioned, this course is one of, if not the only course that is built around the [Covenant][3] .NET based C2 server, by Ryan Cobb of Spectreops. If you don't know Spectreops, they are the team that authored [some of the most used tools][11] in the industry. That's quite some credentials pushing the development of this C2 if you ask me.



For most, I believe 60 days would be a comfortable timeframe to complete the course. But if you have a ton of free time to study or have prior experience, go for the 30 day package.



---



## The Competitors



This might be why you're here isn't it? You may be interested in taking up a Red Teaming oriented course, but are considering between several options, and hence are googling around for reviews to decide which you should take. Understandably due to how new this course is, reviews on the RTO course may not be as easily found as some of the competition. Hopefully this section will help a little with your decision making. 



Before going on to read this section, please note that I may have some insights on the following courses and did some research, but have not taken the following courses (or not yet anyway), so take the following with a pinch of salt. 




### Pentesteracademy - Certified Red Ream Professional (CRTP)



This is a beginner certification which introduces the student to the world of AD exploitation. It covers most of the basic topics and has a fairly heavy emphasis on the command line and powershell. It however does not teach you how to use a Command & Control (C2) server.



Most CRTP holders I've spoken to says this course/certification is easy and I should take it, and  I agree that they do have pretty good study materials. But however I'm fairly serious about wanting to get good at this red teaming thing, so an "easy" cert was not what I was looking for.



If you want a quick resume filler or just want to learn the basics of  AD exploitation, this would definitely be the one to go for.



[Link][6]



### Pentesteracademy - Certified Red Ream Expert (CRTE)



It's a sequel to the above CRTP, expanding on the concepts with a few more techniques, and is more of an intermediate level course which requires some prior AD exploitation knowledge before enrollment. I would have seriously considered taking this one but I had almost zero knowledge on AD exploitation back then.



[Link][7]



### eLearnSecurity - Certified Penetration Tester eXtreme (eCPTXx2)



This is a course which I have purchased  but have yet to start working on. Based on the course materials, this mostly overlaps with the CRTO's syllabus, but  goes a bit further. According to [this review][12] written by a guy who has both CRTO and PTX(v1), he rates them both as *intermediate* in terms of difficulty. But I would definitely say the PTX is tougher.



[Link][8]



###  Offensive Security - Experienced Penetration Tester (OSEP)



This is the grand daddy, the only certification course rated as *hard* based on the above review(gosh he has done everything). On top of active directory exploitation, this appears to be VERY defense evasion heavy, which is great because in a real Red Teaming engagement, you must be able to perform your activities without being caught by various blue team tools and software.



[Link][9]



### Pentesteracademy - Certified Enterprise Security Specialist (PACES)



I have very limited information on this one, but it seems to be of a high difficulty as well.



[Link][10]


---

## RTO in a nutshell

  

**The Good:**

- Dedicated friendly and active slack channel where the man himself is there to assist. When he is not around, the fellow studens are really helpful and friendly as well
- Lab connection is fast and stable, load balancing measures are in place to prevent overloading of students.
- Lifetime access to the latest course updates
- Certification does not expire
- Teaches you how to use a C2

  
  
  


**Room for improvement:**

- Does not come with a certificate, just a badge. Zero-Point has a really nice logo so a certificate with would look pretty neat in a CV.
- Covenant is still under development(v0.7 as of time of writing), where there are some instability issues and bugs, and it can cause some frustration here and there. There are some QOL improvements that are available to RTO students which I will not share here :)
- Honestly I cannot find any faults with this course, because I have nothing but praises for it.



---



## The Exam



I took the exam at the end of March.  I had not finished the labs by this point of time, and had a few things I haven't learnt. But I was running out of time due to having another course lined up, and the next suitable exam date was a month away, so I decided to just go for it.



At the start time, my VPN connection files were sent to me via email promptly and my connection was made. All 4 flags were actually fairly straightforward with no monkey business. Either you knew your stuff or you don't.



In less than a few hours, I had the first flag under my belt. However, due to some strange issue, I was stuck at a particular task for about 24 hours(including sleep and meals of course). I had consulted the course materials, the tool documentation and various reputable guides and blogs on the topic, but the commands used just could not work. In the end, I could only achieve it via some other weird way. It was a very straightforward task, but till today, I still don't know if there was an issue with the exam machine, my tool, or just me being bad at what I do. Perhaps I will never know.




Once I got through, the second and third flags fell rather quickly, allowing me to get my passing score by the 30th or so hour. By then, I was tired and fairly pissed at the issues I was having(I had to reset Covenant 3 times during my exam in total because everything became unresponsive, and start from scratch to regain my progress). I knew where the last flag was, and how to get it, but Covenant decided to crap out on me again, so I called it a day.



All in all, my total exam time was definitely much slower than most(I read that the average is below 24 hours comfortably). If not for the issues I faced, I believe below 10 hours was a very realistic target. Perhaps even faster if I actually completed the labs prior to the exam, as there were some things I had to learn on the spot.



Of course, passing the exam alone did not equate to the CRTO certification, so I went back to the labs and spent the next day or so finishing up what I was missing.



---



## Some final thoughts

Overall, I think this is by far one of the best courses I have ever done, as well as the most fun(and sometimes frustrating). It's cost may seem high at first compared to the offerings from for example Pentesteracademy, but don't forget this is both a beginner AND intermediate course in one.



I would definitely recommend this to anyone who is genuinely interested in getting in the world of Red Teaming and Active Directory exploitation. If you have complete the labs, you definitely would have more than enough knowledge and skills to pass exam. If anything, the labs are harder than the exam itself!



The eCPTXv2 and OSEP are currently on my to-do list, so I may be able to provide more comparisons based on first hand experience in future.



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
[11]: https://specterops.io/resources/research-and-development
[12]: https://github.com/ryan412/ADLabsReview
