---
layout: single
title: SANS SEC760 - Advanced Exploit Development for Penetration Testers Review
date: 2020-03-28
classes: wide
tags:
  - Review
  - SANS
  - SEC
---


Wow! This is a course I’ve been wanting to take since I took my first SANS course, SEC560, in March 2018. There don’t seem to be too many reviews for this course, so I hope to do some justice. Let’s dive in.

The recommended prerequisites are exhaustive: SEC660, FOR610 (mentioned in the pdf), multiple programming languages, fuzzing, reverse engineering code, etc. At this point I did not meet all these recommended requirements, I only started my journey in 2018. I did take FOR610, SEC660, Offensive Security’s CTP, and a few assembly/reverse engineering classes which did help. 


### Day 1: Exploit Mitigations and Reversing with IDA
The [syllabus](https://www.sans.org/course/advanced-exploit-development-penetration-testers) for day 1 is very accurate. There are almost 95 pages right upfront covering exploit mitigation techniques (what they are, how they work, etc.) that have been implemented all the way from XP SP2 through Exploit Guard in Windows 10 replacing EMET. While one safeguard may easily be bypassed, how would you bypass multiple safeguards? The more you understand the safeguards the better your chances of finding those vulnerabilities. Here is a table of [Mitigation Comparisons](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/exploit-protection#mitigation-comparison)

Next was an IDA Pro Introduction. SANS was able to negotiate with Hex-Rays for v7.4 Pro licenses to be used in class. Having only used older free versions of IDA before this was awesome. The overview was really a refresher for navigating IDA, jumping between views, functions, etc. The lecture for it lasted maybe 10 minutes followed by the first lab. Following that was some brief coverage of basic anti-debugging techniques, followed by a deep dive info remote debugging with IDA servers, and a lab setting up a remote debugger. The lab consisted of analyzing of elf file, finding the backdoor, and creating a JMP SRP to pop the bind shell. 

Following that we spent some time with FLIRT and FLAIR. This section was short, but the lab resulted in creating our own sig file for a stripped binary, so we’d be able to resolve function names. Pretty awesome, however creating sig files for CTF usage (or Malware) would be pretty time consuming. And finding them online is a risk, you essentially have to trust that the author has done their due diligence and provided legitimate work (granted that goes for every hacking/security tool).

The first day’s lectures ended with IDA automation: IDC, IDAPython, IDA Plugins, and Toolbox. The last lab ended with creating an IDAPython script that’d assist with SEH Overwrites. 


### Day 2: Linux Application Exploitation
Day 2 sounds exciting, unfortunately that’s all there is to it… sounds it. It always seems that courses which have linux “exploitation” always end up covering topics for both linux/windows (mostly memory management) and then you’ll do a few obscure exploits and pat yourself on the back and it’s a wrap. It’s a joke. SANS’ premier pen testing & exploit development course, SEC760, was the same as dozens of other courses. The day started out covering the heap: what is it, how does memory get allocated, freed up, chunking, bins, etc. Then there was a lab exploring malloc/strcpy/exit with gdb. Awesome, getting into heap exploitation! I’m excited, the first 2 labs were REALLY good! Props to SANS. 

After that things took a turn for the worse. We were given a file (DEFCON 18 CTF Prequal) that we had to Reverse Engineer (RE) with IDA and then write an exploit for to gain admin access within the app. I stumbled along the RE portion as it’s not my strong skillset. But I was able to follow with the book and understand the function calls and program logic with good explanation from the instructor. However, the exploit was surprisingly an issue. From the work to RE the binary you know how many characters you need to overflow the buffer, where null bytes go, username & password field lengths, etc. You would think this part would be easy… Well when this CTF was ran by DEFCON there was a backend database, something SANS has not replicated, and SANS’ fix was to create 2 files which the program references. Well SANS’ intended way to write this overflow was with a buffer of 114 bytes followed by the 20-byte username field length, empty password hash, user permissions, and null byte. However, after no one in the class (instructor included) was able to solve it, we moved on. Except the person sitting next to me, he spent the next few hours digging into the program more. Turns out the overflow causes some weird things to happen and only the first byte of the username is read and changed, but the password hash and permissions do update.  While it’s a cool concept, if it doesn’t work as intended update your content.

After that fiasco we moved onto exploiting bss segments and a very short lab for it. Finally, we finished the day up with exploiting format strings from printf/fprintf/etc using string specifiers such as %x for hex and %n. The exercises were fun to do (very frustrating to find where you fat fingered something!) but not too sure how realistic it is. That last exercise was the only one which had ASLR, not really an advanced exploitation day (excluding IDA) for me. I learned some things I didn’t know before but SEC660’s Linux day was more informative. 


### Day 3: Patch Diffing, One-Day Exploits, and Return-Oriented Shellcode
After day 2 I had high hopes for day 3, and they were exceeded; Patch Diffing, creating 1-day exploits, and more ROP. The day began with a quick refresher of Return-Oriented Programming (ROP); however it was expected that you knew what ROP was, and how to create ROP gadgets. Then there was an exercise with a vulnerable SUID binary which would open a file to read and we had to find the what would cause it to crash and then build and exploit which used ROP to kick off our shellcode. From there we moved into patch diffing. The first lecture binary diffing tools (bindiff, visual diff, patchdiff, etc) as well as analysis methods and views. This led into an example of a small binary (not a patch) to work on technique and get a feel for the tools, we used bindiff5. Finally, we moved into actual patches from Microsoft. There was some background given on patch/update cycles, historical service pack knowledge, patch research, and patch extracting. 

It was around noon and after lunch when we jumped into the exercises which finished up the day. There were 2 patch diffing exercises, then a discovery and weaponizing exercise, and finally one last diffing exercise. The first lab covered MS07-017, which was awesome because another course I took covered creating an exploit for this vulnerability. SEC760 did not cover creating an exploit, more diffing the patched & unpatched dll, discovering what was different, and how the changes fixed the vulnerability. The next two labs covered CVEs from 2016 on Windows 10 x64. In the 3rd lab we discovered the vulnerability using procmon to identify missing files, which led to Social Engineering a user to run a malicious update script to download the missing dll to a writable path the program was looking in. The final lab covered a CVE in which multiple Windows OS versions needed the patch. This lab was fun and involved finding the vulnerability among many changes. Toward the end of the day I felt much more comfortable with IDA and bindiff.


### Day 4: Windows Kernel Debugging and Exploitation
Symbols. Our instructor said the most annoying part of the day is dealing with symbols, he was right. Almost half the class struggled with networking issues and forcing symbols to download, or reloading symbols. What are symbols you ask? Symbol files contain data that is helpful when debugging a process (using windbg) but are not needed while running the binary outside of a debugger.

Anyways this day was ALL about the windows kernel. The day began with covering user-mode vs. kernel-mode, windows subsystem, common dlls and functions, system service dispatcher, HAL, and Kernel Pool memory. Next up was exploit mitigation developments for windows 8-10. Finally, we got to debugging with Windbg, since Olly and Immunity are Ring 3 debuggers and Windbg allows visibility into Ring 0. The first dozen pages or so covered navigation around Windbg’s interface, and then we jumped into 2 exercises. The first exercise was getting remote debugging set up, just go with VirtuaKD and save yourself some hassle. The next lab was split into two; the first part was diffing (same idea as day3) a patch for a kernel driver, the second part was debugging the vulnerability and exploiting it. Next up was Kernel attack techniques, these mostly involved HAL and access tokens. Finally, was a lecture and lab covering a vulnerability where input from user-mode was passed to the kernel driver


### Day 5: Advanced Windows Exploitation
The last day of lectures covered Advanced Windows Exploitation and involved LOTS of Windbg. The first section covered the early days; pre and post XP SP2/2003. We then jumped into topics covering modern heap exploitation from Windows Vista/8 and onwards. Next was a demo of heap spraying, specifically DOM Element Property Spray (DOMS), to exploit an Internet Explorer vulnerability. 

The last topic to be covered was Use-after-Free (UAF). First, we had a walkthrough, it was long…like VERY long. The instructor would let us work our way through the book, stopping us every 30 minutes or so to cover what we went over. After the walkthrough (50+ pages) was a follow up exercise of creating an exploit for the vulnerability. Finally, the day ended in an IE11 vulnerability which allowed full ASLR bypass when all modules were rebased, I did not finish this exercise in the class but did later on at home.


### Day 6: Capture the Flag
The CTF had maybe 3 questions from the SEC660 CTF, I brought the hashes, but they weren’t worth many points. The CTF was a ton of fun and the team of 4 I was on all came away with coins, along with the top scoring individual not on our team. The CTF focused heavily on days 1, 2, 4, 5, and some SEC660 topics. My team was formed with 3 people who were pretty good with IDA (much better than me) and REing experience. We grabbed the lead right out of the gate and held it the entire time. 

![](/assets/images/sans/sec760_ctf.png) ![](/assets/images/sans/sec760_coin.png)
