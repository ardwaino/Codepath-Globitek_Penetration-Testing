# Project 8 - Pentesting Live Targets

Time spent: **5** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each color is vulnerable to only 2 of the 6 possible exploits. First discover which color has the specific vulnerability, then write a short description of how to exploit it, and finally demonstrate it using screenshots compiled into a GIF.

## Blue

Vulnerability #1: Session Hijacking

Description: Tried out same vulnerability on all three site, finally worked on blue site. We were given this tool to change php in a previous unit, so used the same tool.  

<img src="https://github.com/ardwaino/Week-9-Pentesting/blob/c73e31701976483041ee0fb837802a7032e88b28/Session_Hijack_Part1.gif">

In the above gif, I logged into admin on blue site on opera browser, and then found the session id once logged into admin.

<img src="https://github.com/ardwaino/Week-9-Pentesting/blob/c73e31701976483041ee0fb837802a7032e88b28/Session_Hijack_Part1.gif">

Now, I take the previously found admin session id and use the same change session ID tool in firefox and change the normal user's session id to the logged in user's. I click the log in button, and voila, we are in.


## Green

Vulnerability #1: Cross Site Scripting

Description: We were given an XSS script in the assignment by Codepath, we need to find a way for the user to input this stored XSS attack so that when the admin goes to the correct webpage, an alert pops up. The contact page seemed like a good place to start, and I eventually, through trial-and-error figured out the green site had a vulnerability in this aspect.

<img src="https://github.com/ardwaino/Week-9-Pentesting/blob/c73e31701976483041ee0fb837802a7032e88b28/Cross_Site_Scripting_Part1.gif">

In the above gif, I put in the XSS code given into the contact along with a set a name and email including a portion of my name. As well as changing the given code to say Shreyass found the XSS rather than Mallory. I submit this feedback on the user-end in Firefox.

<img src="https://github.com/ardwaino/Week-9-Pentesting/blob/ff81952687cc49643b612b93f44df2621631dbec/Cross_Site_Scripting_Part2.gif">

I now log in to the site and navigate to the feedback portion of the site. I get alerts from previous exploits of the vulnerability as well as mine, that says Shreyass found the XSS.


## Red

Vulnerability #1: Insecure Direct Object Reference

Description: Any page that has a list of things, addresses, names, phone-numbers, are likely battleground for IDOR to take affect. After clicking through the list of names in the salespeople tab, I saw how the ids changed from one person to the next, I figured that one of the sites would have an unreachable user/name. On blue and green, when trying to implement the same thing, I was taken back to the salespeople page, however on red, I was able to access a user who had an id above the number of ids I saw on the other pages.

<img src="https://github.com/ardwaino/Week-9-Pentesting/blob/ff81952687cc49643b612b93f44df2621631dbec/IDOR_Part1.gif">

In the logged in side, I navigate to the salespeople tab and check for users that are not visible/public to the general user, codepath kindly pointed out that testy mctesterson was not public yet.

<img src="https://github.com/ardwaino/Week-9-Pentesting/blob/ff81952687cc49643b612b93f44df2621631dbec/IDOR_Part2.gif">

On the genral user's side, I attempted to change the id number above the list of ids onteh other sites, which in this case, is 10. This allowed me to view Testy Mctesterson who was not public yet.

## Notes

Describe any challenges encountered while doing the work
Trial-and-error takes some time :)

