---
layout: post
title:  "Why we need Intrusion Detection System?"
date:   2013-2-23 00:08:19 +0530
categories: lectures
author: Ishwerdas
image: ids.jpg
permalink: "/lectures/:title.html"
comments: true
---

Antiviruses and Firewalls are the gatekeepers, they try to keep enemy out but what if enemy has already entered? What to do of the enemy within? 

Any country like India would understand the need of having, at least, two armed forces: one that stays on borders and tries to keep the enemy out and another that looks at the enemy within. Indians have the third largest standing army but no matter how strong it is, still intruders/terrorists get inside through the borders and wreak havoc. 26/11 and recent Gurdaspur Firings are good examples of breaches in Indian border security. 

Similarly, we may have a strict firewall and a very advanced AntiVirus, still all you get is an illusion of security. Now, I am not saying that they are not useful but **it's foolish to expect that no one will ever bypass your security**.  

Firewalls have little doors and windows inside them, the windows through which you are able to access the internet, watch a video or send an email. Antiviruses are good enough to detect only the viruses, that are already known to them and the weakest link in your security are humans. Humans that have emotions, prejudices, egoes and are prone to social engineering. 

**So while the Firewalls and Antiviruses try to keep the bad stuff out of the door, Intrusion Detection Systems try to detect malicious activity that has already entered the system.** Intrusion Detection systems start when the system has failed to keep the bad stuff away.

**So how do intrusion detection systems work?**

IDSs try to check for an activity that could be thought of as malicious and makes a guess if it's an intrusion or not. For example there's an IP that's hitting at multiple ports, now why would someone do that? 

The only obvious answer we can think of is someone trying to check which of the ports is open. Hitting all ports is similar to someone trying to open all the doors in hallway, obviously a strange activity that deserves attention. However is it really an intrusion or not? The answer would be we can't be 100% sure. Here's the point where **tuning** comes in. Intrusion Detection System is as much as a technology as much as it is a policy. Suppose we have configured our IDS initially and for the first week it gave way too many alerts, most of them being false positives, we would go back to configuration files and tune it, change it until we have the perfect balance. 
