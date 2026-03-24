---
layout: post
title: Pre Security - Introduction to Cybersecurity
date: 2025-11-29
description: An introduction to pre-security
tags: presecurity review
# categories: sample-posts
# thumbnail: assets/img/9.jpg
---

## I. Introduction to Cybersecurity
### A. Offensive Security Intro
#### 1. What is Offensive Security?

* In this lesson, it is said that: *to outsmart a hacker, you need to think like one*.
* Offensive Security involves breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access.
* **Goal:** to understand hacker tactics and enhance system defenses.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/presecurity-intro-1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

**Answer:** `Offensive Security`

---

#### 2. Hacking Your First Machine

* In **TryHackMe**, virtual machines are created to simulate environments that serve as practical complements to lessons.
* A fake bank application is prepared that can be safely hacked.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/presecurity-intro-2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

##### a. Your First Hack

###### --- dirb Method ---

* The goal is to find a way to hack the FakeBank application to steal money
* One of the easiest way an application can be hacked is to look for hidden features in the application
* Sometimes, applications will expose sensitive functionality to users via secret URLs
* If secret URLs can be found, actions that a regular user can't do can be perfomed.

* To find hidden URLs, a tool called **dirb** will be used.
    * **dirb** uses a brute-force approach
    * It will take a *list of potential page names* and will test it one by one if they exist in the website

* Using **dirb** to Find Hidden Website Pages
    * To use **dirb** write the `dirb` command followed by the URL of the website to be brute-forced
    * `dirb http://fakebank.thm`

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/presecurity-intro-3.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/presecurity-intro-4.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

* A simple breakdown of the output:
    * ``URL_BASE``
        → the URL given to the tool
    * ``WORLDLIST_FILES``
        → shows the location of the wordlist file used by the tool, which contains common page names that will be tested during the brute-force attack
        → the tool used the default wordlist included with the tool, located at the mentioned path

**Question:** Dirb should have found 2 hidden URLs. One of them is http://fakebank.thm/images. What is the other one?

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/presecurity-intro-5.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

**Answer:** `http://fakebank.thm/bank-deposit`

* The previous link leads to a secret page that allows adding funds to a bank account.
* From this page, it should be allowed to add funds to a bank account with the number 8881 (the bank account)

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/presecurity-intro-5.5.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

* If the transfer is successful, a pop-up should appear with some green words.
**Question:** Input the green words as the answer to this question.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/presecurity-intro-6.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

**Answer:** `BANK-HACKED`

**Achievement:**
* [https://tryhackme.com/room/offensivesecurityintrokK?utm_campaign=social_share&utm_medium=social&utm_content=share-completed-room&utm_source=copy&sharerId=68f5e3baaa4bd512a31cc4b3](https://tryhackme.com/room/offensivesecurityintrokK?utm_campaign=social_share&utm_medium=social&utm_content=share-completed-room&utm_source=copy&sharerId=68f5e3baaa4bd512a31cc4b3)


###### --- End of dirb Method ---
###### ------------------------------------------------------------
###### --- Gobuster Method ---

* A command-line application called **Gobuster** is used.
* Gobuster brute-forces FakeBank’s website to find hidden directories and pages.

  * Gobuster takes a list of potential page or directory names and tries accessing the website with each of them.

###### i. Step 1: Open a Terminal

###### ii. Step 2: Use Gobuster to Find Hidden Website Pages

* Most companies have an **admin portal page**, giving staff access to admin controls.
* Due to human error or negligence, these pages may not be private, allowing attackers to find sensitive pages.
* Gobuster flags valid pages using **Status: 200**.
* Key flags:
  * `-u` → target website
  * `-w` → wordlist

###### iii. Step 3: Hack the Bank

* A secret bank transfer page exists: `/bank-transfer`.
* From this page, an attacker has unauthorized access and can steal money.
* **Mission:** transfer **$2000** from bank account **2276** to **8881**.
* If successful, the new balance is reflected on the account page.

**Answer:** `BANK-HACKED`

###### --- End of Gobuster Method ---

---

### Careers in Cybersecurity

* **Security Engineer** – Designs, monitors, and maintains security controls, networks, and systems to prevent cyberattacks.

**Achievement:**
* [https://tryhackme.com/room/offensivesecurityintro?sharerId=68f5e3baaa4bd512a31cc4b3](https://tryhackme.com/room/offensivesecurityintro?sharerId=68f5e3baaa4bd512a31cc4b3)

---

### B. Defensive Security Intro

* Also known as **Blue Teaming**.
* When defensive security fails, consequences can include ransomware attacks, healthcare disruptions, and massive data leaks.

**Answer:** `Blue Teaming`

---

#### 1. Responsibilities of Defensive Security

* **Monitoring and Detecting**
  * Continuous observation of networks and systems.
  * Example: logins from another country while the employee is based in London.

* **Incident Response**
  * Initiated once suspicious activity is confirmed.
  * Includes containing threats and restoring normal operations.

* **Threat Intelligence**
  * Collecting information about attacker methods, targets, and trends.
  * Helps strengthen organizational defenses.

* **Vulnerability Management**
  * Fixing system and software flaws to reduce attack risks.
  * Can be done manually or with automated tools.

* **Investigation and Analysis**
  * Separating normal activity from suspicious behavior.

##### Defensive Security Roles

* **Bob – SOC Analyst**
  * Monitors events and identifies suspicious behavior.
  * Frontline defense.

* **Aaliyah – Incident Responder**
  * Investigates and responds to active incidents.
  * Shares lessons learned to prevent future attacks.

* **Zoe – Security Engineer**
  * Develops and maintains security tools and systems.

* **Bill – Digital Forensics**
  * Gathers and analyzes evidence to understand attacker behavior.

**Question:** An attack has been detected on an organization’s network. Who responds?

**Answer:** `Aaliyah`

---

#### 2. Defensive Security in Practice

* Organizations use **Defense in Depth** (layered security).

##### Examples of Defensive Measures

* **Employee Training**
  * Focus on phishing awareness and human-factor risks.

* **Intrusion Detection Systems (IDS)**
  * Monitor and alert on suspicious network or system activity.

* **Firewalls**
  * Control which traffic is allowed or blocked.

* **Security Policies**
  * Enforce strong passwords and restrict risky access.

##### Key Technologies

* **Security Operations Center (SOC)**
  * Central hub for monitoring and incident response.
  * Daily tasks include reviewing alerts, investigating anomalies, and responding to incidents.

* **SIEM – Security Information and Event Management**
  * Centralized system for collecting and analyzing security data.
  * Enables faster and clearer investigation.

**Question:** What is the abbreviation for *Security Operations Center*?

**Answer:** `SOC`

---

#### 3. Practical: Defend FakeBank

* Hands-on investigation of an active attack using a SIEM.

##### Scenario

* You join the FakeBank defensive security team.
* Investigate suspicious events and protect customers.

##### What I Did
* Opened **Investigate** on a Web Discovery Attack.
* Attack details:
  * Started: **July 14, 2025 – 10:21:39 AM**
  * Duration: **16 minutes 32 seconds**
  * 31 URLs accessed (likely Gobuster enumeration)
  * Source IP: **Moscow, Russia** (malicious)

##### Recommended Actions

* Block source IP
* Review admin panel logs
* Implement rate limiting
* Update WAF rules
* Source IP investigated: `32.122.195.63`

##### Rate Limiting

* Time window: **60 seconds**
* Max requests: **50 per window**
* Prevents brute-force and excessive endpoint abuse.

##### WAF Rule Update

* **Rule:** Block suspicious enumeration attempts

* Examples include:
  * Guessing admin paths
  * Sequential ID probing
  * Token or API key guessing

* WAF detects and blocks repeated or patterned requests.

**Final Flag:** `THM{FAKEBANK-SECURED}`

---

### C. Careers in Cyber

#### 1. Introduction

* Cybersecurity roles are in high demand with competitive salaries.

#### 2. Security Engineer

* Designs and maintains security controls and systems.
* Develops defenses against web, network, and evolving threats.

##### Responsibilities

* Test and screen security measures.
* Monitor networks and mitigate vulnerabilities.
* Identify and implement optimal security systems.

##### Learning Paths

* SOC Level 1: [https://tryhackme.com/path/outline/soclevel1](https://tryhackme.com/path/outline/soclevel1)
* JR Penetration Tester: [https://tryhackme.com/path/outline/jrpenetrationtester](https://tryhackme.com/path/outline/jrpenetrationtester)
* Offensive Pentesting: [https://tryhackme.com/path/outline/pentesting](https://tryhackme.com/path/outline/pentesting)

##### Career Guides

* [https://tryhackme.com/r/careers/security-engineer](https://tryhackme.com/r/careers/security-engineer)
* [https://tryhackme.com/r/resources/blog/become-security-engineer](https://tryhackme.com/r/resources/blog/become-security-engineer)
* [https://tryhackme.com/r/resources/blog/interview-with-security-engineer](https://tryhackme.com/r/resources/blog/interview-with-security-engineer)
* [https://tryhackme.com/r/resources/blog/security-engineer-interview-guide](https://tryhackme.com/r/resources/blog/security-engineer-interview-guide)
* [https://tryhackme.com/r/resources/blog/richard-success-story](https://tryhackme.com/r/resources/blog/richard-success-story)

**Achievement:**

* [https://tryhackme.com/room/careersincyber?sharerId=68f5e3baaa4bd512a31cc4b3](https://tryhackme.com/room/careersincyber?sharerId=68f5e3baaa4bd512a31cc4b3)

---




