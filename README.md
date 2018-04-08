# Project 8 - Pentesting Live Targets

Time spent: **2** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection (SQLi)

- Insert SQL into the id field. I put in `' OR SLEEP(5)=0--'` to make the database stall for 5 seconds.
<img src="Blue - SQL inject.gif" width="800">

Vulnerability #2: Session Hijacking/Fixation

- Use the php script to get the session ID, then copy it into another browser window's php script to change the session ID to the first session ID.

<img src="Blue - session hijacking.gif" width="800">

## Green

Vulnerability #1: Username Enumeration

- the field for `span` is failure if the username is correct, but failed if the username doesn't exist, allowing the attacker to identify if a username exists in the database or not.

<img src="username_enumeration.gif" width="800">

Vulnerability #2: Cross-Site Scripting (XSS)

- Insert `<script>alert(‘Josh found the XSS!');</script>` in the feedback form, they get hit by it when they open their admin feedback page.

<img src="green - stored XSS.gif" width="800">

## Red

Vulnerability #1: Cross-Site Request Forgery (CSRF)

- Insert http://jushkem.github.io/assets/js/feedback.html in the feedback form, when they click it the form is changed.

<img src="red - CSRF.gif" width="800">

Vulnerability #2: Insecure Direct Object Reference (IDOR)

- Changed the id field in `https://35.225.89.208/green/public/staff/salespeople/show.php?id=10`. If you enumerate it past 9, you get salespeople that should not be public.

<img src="red - IDOR.gif" width="800">

## Notes

Describe any challenges encountered while doing the work
