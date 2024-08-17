---
title: WINDOWS FORENSICS 
date : 2024-05-28 02:21:00
category: [FORENSICS]
---

# WALKTHROUGH
A windows machine has been hacked, its your job to go investigate this windows machine and find clues to what the hacker might have done.

# Challenge Question:
Whats the version and year of the windows machine?
Answer: `Windows Server 2016`
![Alt text](/assets/img/kioptrix/intro.png)


Q2 Which user logged in last?
Answer:`Administrator`
Challenge Question: When did John log onto the system last?
Answer: `03/02/2019 5:48:32 PM`
Challenge Question: What two accounts had administrative privileges (other than the Administrator user)?

command `net localgroup administrator`

Answer: `Jenny, Guest`
Challenge Question: When did Jenny last logon?
Answer: `Never`