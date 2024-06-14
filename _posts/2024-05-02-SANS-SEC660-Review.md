---
layout:     post
title:      "SANS SEC660 Review"
date:       2024-05-02 23:00:20
author:     J
summary:    SANS eh?
categories: Exploitation
thumbnail:  graduation-cap
tags:
 - Binary Exploitation
 - SANS
 - GIAC
 - GXPN
---



# THIS IS STILL A DRAFT AND IS SUBJECT TO EDITS, PLEASE COME BACK LATER. BUT IF YOU REALLY WANT TO READ,  JUST KEEP IN MIND THAT THIS IS NOT THE FINAL POST



It's been a long time since I wrote about a new certification. After a 2 year hiatus, I guess I'm back!



Recently I have had the opportunity to take the [SEC 660: Advanced Penetration Testing, Exploit Writing, and Ethical Hacking][1] course, and take the associated exam, the [GXPN (GIAC Exploit Researcher and Advanced Penetration Tester)][2].



Before I go on, just bear in mind that I have been in the Cyber Security Industry for almost 6 years at the point of taking the course/exam, most of which were spent in the Penetration Testing and Red Teaming space. I also studied Forensics, and have been through the OSCE and about 60-70% of the OSED materials. So I can say I'm fairly comfortable with a decent chunk of the topics.


In this post, I'll share my experience with the course and exam. Uncensored, Au Naturel without sugarcoating. These are my personal opinions and does not reflect on the views of my peers or my employer.



## The Course

Let's start with the overview:



The SANS SEC660 course is one of the more technically advanced courses by SANS, and a stepping stone to the SEC760, which is arguably their most advanced course. It is split up into 5 sections, as follows:

1. Network Attacks for Penetration Testers
2. Crypto and Post-Exploitation
3. Python, Scapy, and Fuzzing
4. Exploiting Linux for Penetration Testers
5. Exploiting Windows for Penetration Testers



As unfortunately there wasn't an opportunity for me to take the live course as there wasn't one scheduled near me, so I settled for the OnDemand version, which was fully online through recorded videos. With the course there were "Quizzes", which can be taken multiple times with mostly repeating questions and 2 Practice Tests(only 1 attempt each), which fairly closely mimic the Final GXPN exam in both format and difficulty.



Due to a bad habit of procrastination, I only touched the materials here and there over the first few months. It did not help that the first 3 sections of the course were extremely dry topics. When combined with my short attention span, I just couldn't sit through the hours of videos. 



Come the last month, the pressure finally set in. I figured to use an alternative strategy to drag myself across the finish line. Instead of going through the videos, I'd just power through the books, speed-reading them while writing the the index in Microsoft Excel.



For context, the "Index" when referring to SANS GIAC certifications is a self-written directory of keywords, and where(which book and page) you may find information on a certain topic. When I was done indexing all 5 books, I had over 500 entries in it. My formatting was simple, and would look something like this:



| Book.Pg | Quickfind                       |
| ------- | ------------------------------- |
| 69.420  | PEB - Process Environment Block |



This is good because after I was done, I could quite easily sort the contents in Alphabetical Order for easier searching. Because you know, using a huge stack of books and a stack of papers is much better than Ctrl+F in this day and age. /s



Also, after indexing each book, I would go into the OnDemand course and attempt the quiz, both to test my knowledge and understanding of the material, and the effectiveness of my index. For each question I got wrong, I made sure to update the index to address my blind spots.



After I was able to get full marks on all the quizzes, I decided to use my first Practice Test as a gauge. At this point all I did not touch the labs at all, and sped through the videos just for the last 2 sections of the course at 1.5x speed.




All in all, it took maybe 3 weekends(6 days), plus quite a few hours over the weeknights to get to this stage. There were off days where I'd be too tired after work or want to watch a movie with the wife.



### First Practice Test - 2 days to exam



The test format was quite a bit different compared to the other technical exams I've taken.



The format was such - 60 Questions total, passing score of 67%:

- 3 Hours
- 54 Multiple Choice Questions
- 6 Practical Questions (they call it "CyberLive"), where you access a VM through the test browser to perform some stuff, to answer a MCQ question.
- I believe that the CyberLive questions were more heavily weighted with respect to the final score, I couldn't figure out how much more they were worth but just take it that you should absolutely nail them if possible.



The practice tests can be started on demand, so let's do it. EZPZ right? Also, they do explain the questions you get wrong, so that was really helpful.



I blazed through it, taking ***1 hour 4 minutes*** to clear the first 54 questions. I didn't really take note of how long I took to do the remaining 6 though, But I think less than 3-5 minutes each. The result?



### ![PT1](/images/2024/GXPN/67.png)



What. The. Fuck?



I panicked. I think quite a lot of points were lost to some of the CyberLive questions. I knew what I needed to do but I was not as familiar enough with the specific tools, going by pure memory of the videos. I also realized that I didn't create a cheat sheet of tool commands. So it was back to the drawing board. A question or two were also not clear enough, and only after I got it wrong I got what they were trying to say. Bummer.



With 67%, I really only had a 50:50 chance of passing the actual exam to be honest.




### The aftermath of fear



I went back to refine the index once more, and rewatched the videos demonstrations on the binary exploitation bits where I seem to feel I could do a bit better on(also because they were the really interesting parts). Also made sure to get a half decent cheat sheet on the tools, especially those which were came up during the practice test. It was another 3am night again for me, to the dismay of the wife, who always stubbornly refuses to go to bed without me.



### Second Practice Test - 1 day to exam



The next day after I woke up in the early afternoon, I got lunch and heavily caffeinated and started reviewing the questions I got wrong, both in the past in the quizzes, and the Practice Test. Printed my 15 page index (563 entries, excluding the cheat sheet in case you were wondering), and got to work on the second Practice Test, this time with a physical index.



Based on the pacing of the last test the day prior, I knew that there was waaaaaaaaayy more than enough time to finish the whole thing. So I made a conscious effort to to the following:

- Avoid "I think it should be this" and similar guesswork or the usual elimination shenanigans (Yes reader, I know you do that too). If I had a less than 90% certainty that I had the right answer, I would make sure I searched my index and refer to the book.
- Make sure to click, then read again, then click next. I had the habit of selecting my option then clicking next too quickly, which costed me points previously.
- If I can't find something in the index, or the answer wasn't clear cut in the book(s), spend some time flipping around the entire chapter to see if there's any mention of it.


With this updated index, and my brand new cheat sheet in hand, I managed to correctly answer all 5 CyberLive questions with relative ease this time. Once you take the practice test the first time, you'll know exactly what you need to have in your notes.



The result?



### ![PT2](/images/2024/GXPN/79.png)



Not too shabby, a 12% overall increase from the previous attempt. I also took ***1 hour 45 minutes*** this time to clear the first 54 questions. Slowing down worked, and I still cleared the exam with an hour to spare.



As you can see, the stars are not a true reflection of your understanding of the topic. You can get 5 Stars in one subject one day, and 0 Stars in the same thing the very next day. Probably just means there was only 1 question in that subject or something, I cannot be too sure.



I added some handwritten extra entries to the index and with toothpicks on my eyelids, I forced myself to watch the videos of the earlier sections to get a better understanding. Other than that, I slept better that night.



### The GXPN Exam



I did the exam at home through the ProctorU platform. I would highly recommend it as it gave the following benefits:



1. You didn't have to use some Windows XP toaster of a computer at a Pearson Vue Testing Center attached to a monitor and mouse passed down from someone's grandmother.
2. You have your own table, which is a layout you're used to and already have an idea how to place and move your stack of books around.
3. The chair isn't stained with the butt sweat due to nervousness from the hundreds of exam takers before you. (Mesh chairs ftw btw)
4. The air conditioning is at the right temperature you set it at
5. You can have your beverage of choice with you, or beverages.
6. You don't even have to travel!



Just make sure to get their browser(used for proctoring) well in advance. Because their servers seem to be connected via dial-up or something, taking nearly 2 hours to download. I had mine downloaded much earlier, and thankfully I checked the browser again the day of the exam. Because it had to update and take another almost 2 hours to complete.



In any case, the pre-exam verification went smoothly; I had to verify my identification and give the proctor a video tour of my room, and cover my second monitor with a shirt (even though I already disconnected it, because only 1 monitor is allowed)



The exam was of very similar difficulty as the 2 Practice Tests, and again, the CyberLive questions were some of the free-est points you can get. I didn't really take note of the times, but I stuck to the strategy of "slowly but sure of my answers". Based on my call logs, because the wife was the first person I had to tell, it was about 2 hours or so, just like the day before.



In the end, this was my final result:



![ExamResult](/images/2024/GXPN/88.png)



I think I way exceeded my own expectations. I had taken the test 3 consecutive days in a row and recorded a 10-12% increase in score each day. A slight bummer I missed the 90% required to be on the SANS Advisory Board, but oh well.





### Reflections and Takeaways



Looking back, would I have done better, or gotten much closer to a perfect score if I had started earlier? Perhaps. Maybe. Probably. I managed to pass the exam in under a month of studying without touching any of the labs, but by just watching the walkthroughs.



But if I could go back in time and have a do-over, would I have done it any differently? No. Probably not.



The primary reason why I wanted to take the SEC660 was to improve my understanding and knowledge of binary exploitation. I couldn't care less about the stuff in the first 3 sections. I disliked Cryptography back in school, and that hasn't changed over the past half decade. 



Don't get me wrong, what is taught is valuable and very applicable in the real world, but it is not where my focus is on at this point in time. With my limited time and mental capacity to absorb new knowledge, I opted to focus it all on what I really wanted to learn, and I think that's okay.





### Conclusion



Now, would I recommend this course? I would say it very much depends.



There are 3 main considerations to this:

1. Cost
2. Are you in it for yet another cert in your resume, or the knowledge? If both, which is more important to you?



From a cost perspective, even if you have that budget to spend, absolutely not. The cost would be about right for a week long live training course, but not the OnDemand. For that price you could probably get all 3 300-level courses from Offensive Security with change to spare for a short holiday, while coming out with significantly better competencies due to how their exams are structured. I also personally do not believe in expiring certifications and see them as cash cows.



If you are in it for the knowledge, and someone is sponsoring the course, there's no harm going for it. It is really quite well designed. If you actually follow ALL the labs, I think you'd have half the OSED concepts down.



In terms of difficulty, it's not exactly a very difficult course. The contents cover a very good breadth, with an emphasis on the good stuff at the back. Stephen Sims in particular, is an excellent instructor and made the content quite easy to follow and interesting.



If we're being vendor agnostic, based on my personal experience, I would place it above the OSCP, carrying on where it left off. The GXPN is on a similar level or slightly higher to the now-retired OSCE, but below OSED.



For the exam, I would say it is 55% how good your indexing and searching skills are, 35% how well you understand the materials, and 10% whether you have your lucky red underwear on when guessing that few questions which look totally alien to you.





[1]: https://www.sans.org/cyber-security-courses/advanced-penetration-testing-exploits-ethical-hacking/
[2]: https://www.giac.org/certifications/exploit-researcher-advanced-penetration-tester-gxpn/