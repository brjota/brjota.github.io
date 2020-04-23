---
layout: single
title: Cracking the Perimeter & OSCE Certification Review
date: 2020-04-12
classes: wide
tags:
  - Review
  - OSCE
  - OffSec
---


### Prior Experience
 - Nothing related to the course syllabus besides going through OSCP
 
#### 3 months out
- I started prep for OSCE with what everyone recommends if you do not already know Assembly, SLAE. I was also following along with Tulpa's OSCE/CTP Prep Guide knocking out the videos while working through the lesson plan. I subscribed to SecurityTube for the 3 months instead of purchasing the course, also never took the certification
    - [SLAE](https://www.pentesteracademy.com/course?id=3)
    - [Tulpa's OSCE/CTP Guide](https://tulpa-security.com/2017/07/18/288/)

- After I finished Tulpa's Guide I went over abatchy's OSCE Plan to supplement what was not covered
    - [abatchy's OSCE Plan](https://www.abatchy.com/2017/03/osce-study-plan)

- While working my way through both guides I would also do the exercises, it's one thing reading a tutorial and saying "yea that makes sense, I can do this" and it's another actually doing it

- I also worked on vulnserver
    - [Vulnserver](http://www.thegreycorner.com/2010/12/introducing-vulnserver.html)

#### 7 Dec 19
- I started my lab, 60 days paid for by work. I was initially quite surprised on the lab layout coming from OSCP, it was...smaller. Each machine had a purpose, well they had many purposes, covering multiple topics from the syllabus

- I worked my way through the lab, not encountering to many issues. I was using the PWK 2018.3 VM, no updates installed. The most issues I encountered were due to me mixing numbers around in my head

- The forums are not as active as PWK, however there is some good information in there. I ended up reading all the posts just to see if I could find something I might have missed. The InfoSec Prep Discord also has an OSCE section. There is 10+ years of knowledge in the CTP posts, some of it is VERY helpful. read it and take notes
    -[InfoSec Prep](https://discord.gg/9Nktb9z)

#### 22 Dec 19
- I finished my way through the material, in total I covered the course content 3 times. First time I would read PDF, watch the videos, do the exercise, and take notes. Second time I'd read pdf, did the exercises, watched videos, editing any notes I thought had to be. Three times was probably overkill, 2 is good to make sure you understand the concept they are trying to teach. After that I'd recommend rewriting exploits from expoloit-db

- I also watched mut's NNM presentation on youtube maybe 3 times
    - [HP NNM Exploit](https://www.youtube.com/watch?v=gHISpAZiAm0&feature=emb_title)

#### Exam Time! 22 Jan 20
- Scheduling times are weird, there are like only 3 time slots a day and they start at weird hours. Mine started at 0700
- 0700 and the email shows up in my inbox. Unlike OSCP, OSCE is not proctored so there was no time spent with that. Just connected to the VPN, got the Control Panel Link and got started!
- The instructions were VERY clear. Unlike OSCP where your objectives are "root this box" and its up to you to get there, OSCE is the opposite. You are told what to do, but can you do it?

- 48 hours is a LONG test, make sure you have food ready, caffeine, breaks planned, and take your sleep!
    - 0700 - Exam Starts
    - 2347 - YES, it literally took me over 16 hours to get ANY points. Granted I worked through different boxes until I finally made any progress and got to this point but DAMN. 10+ hours in I was thinking I'm going to fail (spoiler: I did), but at that point I still had 37+ hours left. Don't stress yourself like I did, there is plenty of time. At this point I had 30 points, 45 more to go!
    - 0000 - I decided to take a 4 hour nap at this point
    - 0420 - Fueled by caffeine I started back up with one of the 15 point boxes
    - 0935 - 15 more points down, 30 to go! 
    - 1123 - It was at this point I found my foothold on the "beast", I really enjoyed this box and the challenges it presented
    - 0450 - Yes, you read that right. I made LOTS of progress, but unfortunately not enough. I was getting hung up with an issue that I never encountered in the labs, and honestly had no idea how to solve. It wasn't an issue that was created by OffSec, more it was my misunderstanding. At this point, what no idea what else to Google to help fix my issue, I called it and went to sleep. I was SO close to passing, I could reach out and touch the finish line

#### Disappointment
- Everyone deals with failure differently. I decided to decompress and take a week off anything Computer Security related
- Afterward I was reviewing my notes and screenshots, decided to fire up vulnserver again and work my way through the vulnerable commands again
    - There are a few good writeups on different ways to exploit for this service. Even if you solve one of the commands, maybe someone else did it differently. Maybe you'll learn something or find a way to improve your code from reading someone else's write up. Read as many as you can, it can only help

#### Round Two! 19 Feb 20
- This time I started at 1300, like last time the email was right on time

	- 1300 - Exam Starts. This time I decided to work on the 2nd 15 point box since I didn't touch it last time
	- 1030 - With 46 hours into the exam and no solution on the beast I called it
	- 1500 - 15 points down. Time to work on the beast again. I thought I did enough prep on how to solve this box, hours worth. However I made almost no progress from my first attempt. Turns out I have the right process down, I just had a fundamental misunderstanding about how debuggers work 

- I failed for something very specific, there was some additional prep I did to make sure I understood why I failed and how to not repeat my mistake. All I'll say is make sure you understand how debuggers work. 


#### Round Three! 18 Apr 20
- I wanted to take this on a Saturday, 0800. For that I had to book my test a month in advance. Ouch.. Booked it mid March

	- 0800 - Exam Starts
	- 0843 - Solved the beast
	- 1135 - Had all my screenshots and documentation for the other 3 hosts
	- 1540 - Lab report was written up
	- 1746 - I reviewed my lab report 3 times, took a hour break and reviewed it a 4th time. Everything looked good so I submitted it


#### Take aways:
- Lots of people say this course is outdated. Valid, considering how old it is. However, you have to walk before you can run. This course has its challenges and forces you to research on your own.
- Failing sucks and failing twice really sucks. Passing after failure is a great feeling!
- If you believe everything should be working, but it's not double check your process. You are doing something wrong somewhere, walk yourself through your exploit dev process. 
- Sometimes deleting your POC and starting fresh will resolve your error. You might be assuming and glossing over your mistake


  [Useful tools, scripts, and goodies I assembled while prepping for the CTP labs](https://github.com/brjota/Courses/tree/master/OSCE)
