---
layout: post
title: CTFs - Pickle Rick
date: 2026-02-03
description: a Rick and Morty CTF, Rick needs help turning back into a human
tags: CTFs
categories: cybersecurity
# thumbnail: assets/img/9.jpg
---

## I. Pickle Rick
* This Rick and Morty [TryHackMe](https://tryhackme.com/room/picklerick) challenge requires me to:
  *  exploit a web server; 
  * and find three ingredients to
    * help Rick make his potion; 
    * and transform himself back into a human from a pickle

### A. What I Did
* I first deployed the virtual machine and explore the web application

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ctf/pickle_rick/1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

---

Before going in to the exploration part, I first thought about the phases of Penetration Testing as a guide on what to do first. 

The phases of Penetration Testing is as follows: 

**Reconnaissance → Scanning → Vulnerability Analysis → Exploitation → Post-Exploitation → Reporting**

* <u>Reconnaissance</u>
  * learning anything as much as possible about the target 
  * *examples*: DNS records, WHOIS, Public IPs, OSINT, ping sweeps, port scanning)
* <u>Scanning and Enumeration</u>
  * identifying vulnerabilities
  * *examples*: port scanning, service and version detection, OS detection, user enumeration
  * *tools that can be used*: nmap
* <u>Vulnerability Analysis</u>
  * identifying weaknesses that can be exploited with the discovered vulnerabilities
  * *examples*: using known CVEs, misconfigurations, weak credentials, outdated software, logic flaws
  * *tools that can be used*: Nessus, OpenVas, Nikto
* <u>Exploitation</u>
  * gaining unauthorized access
  * *examples*: password attacks, web exploits
  * *tools that can be used*: Metasploit
* <u>Post-Exploitation</u>
  * seeing how far this attack can go by:
    * escalating privileges, moving laterally, credential dumping, accessing sensitive data
  * *example*: escalating from a low-privilege user to root/admin
* <u>Reporting</u>
  * reporting findings of vulnerabilities found, risk levels, impact, and even recommendations

---

* With that, I first started scanning the machine for any open ports

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ctf/pickle_rick/2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

I saw that the SSH port and http port is open so I might explore these two further. 

An open SSH port (port 22) is an opportunity for later if I have credentials. On the other hand, an open HTTP port (port 80) can be a good starting place as I can do a lot in that area.

Typing in the ip address in a Firefox browser showed me this web page.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ctf/pickle_rick/3.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

Trying to view its page source code showed me this:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ctf/pickle_rick/4.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

it doesnt really show anything except for a username. i'll take note of this for later

the next thing i can do now that i have a web page is to look for directories i can access using dirb

--- insert pic5 ---

i found out that i can access these webpages. let's see what i can find from these

i found this on the robots.txt path from earlier. a quick google search told me that a robots.txt file tells search engine crawlers to not go there, as per the Robots Exclusion Protocol. 

With that, developers accidentally use it as hide stuff list that reads to pentesters as "please attack these first". it's basically a page where developers don't want people to look at. so it must be important hehe let's take note of this for later

--- insert pic6---

it wasnt much so i maybe i might be missing something. i tried to look at the documentation of dirb and figured out a more specific command i can try. 

one example i can try is to append the `-X` command to also look for webpages that have different extensions. 
--- insert pic 10 ---

a quick google search later for the different extensions for webpages show the following: php, html, js, txt, bak, old, zip, env. so we will use these first.

the command `chuchu` showed that i can access these webpages. 
--- pic 11---

going to the login.php page directly showed me this login page
--- pic 12---

if i remember clearly, when i checked the source code of the page, there showed a username. I can also try to use the random word i saw earlier in the /robots.txt page.
--- pic 13 ---

and i got in!
--- pic 14 ---

it says command panel so maybe i can try some commands. i typed in `dir -a` and it showed the following

--- pic 15 ---

these are all web pages from the website. maybe i can access them by appending the file names to the path of the website, starting from the most suspicious file name

`http://10.48.176.26/Sup3rS3cretPickl3Ingred.txt`

and it showed this: our first ingredient!

--- pic 16 ---

for finding out the next ingredient, i accessed the /clue.txt page and it showed this

--- pic 17 ---

the linux file system is how linux organizes, storers, and accesses files and directories.

/      → everything
/etc   → configs
/home  → users
/var   → logs & web data
/tmp   → temporary stuff
/bin   → commands
/root  → admin home

i can start by going through those directories

trying `dir / -a` showed the directories of the filesystem
--- pic 18 ---

next, i tried if i can use `sudo -l` and use its privileges. and i can!
--- pic 23 ---

so i tried `sudo dir /root -a` and it showed me this
--- pic 24 ---

i tried to use the command `sudo cat /root/3rd.text` to try to display its contents as i think that is the 3rd ingredient but it showed me this
--- pic 25 ---

since this is clearly a file, i can try to use `less` and `more` to view it. `more` didn't work. but `less` did.

`sudo less /root/3rd.txt`

and it showed me the 3rd ingredient!
--- pic 26 ---

trying to find the second ingredient led me back outside the /root directory. another directory i can try is the /home directory. 


trying `dir /home -a` showed rick's account. let's try to snoop there
--- pic 19 ---

trying `dir /home/rick -a` showed this
--- pic 20 ---

i tried the command `less /home/rick/second\ ingredients` to display its contents and it showed me this
--- pic 22 ---

After inputting these answers in the answer fields, I finished the Pickle Rick CTF and turned Rick back into a human!
