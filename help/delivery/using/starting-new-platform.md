---
title: Starting a new platform with Adobe Campaign Classic
description: Learn more about managing deliverability when starting a new platform with Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
---

# Starting a new platform {#starting-new-platform}

Maintaining your domain and IP address reputation is essential. You will find below some advice for setting up a new platform.

Starting to send emails on a new platform is a sensitive step because the platform does not have any history of use and no reputation (when the sending IPs have never been used for this purpose). ISPs are naturally suspicious of IP addresses that have never been used to send email and that suddenly start to send large volumes of email traffic. In effect, spammers generally use "unknown" IP addresses (that is to say addresses that have never been blacklisted) to send the largest possible number of messages before detection.

You cannot expect to reach operational speed in terms of output at the very start of the production phase. Furthermore, you should not attempt to send messages at this rate as it might lead the ISPs to block the sending addresses and to severely compromise the rest of the start-up phase.

Starting a platform often happens when using a list of addresses for the first time and which may not be fully qualified. If you send to invalid addresses or to honeypot addresses this will contribute to diminishing the reputation of the platform. If you have a list of invalid addresses, it is in your best interests to import it into the quarantine table (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) before sending for the first times. If, all the same, you wish to requalify the invalid addresses, it is by far preferable to do this once the reputation of the platform is established and bit by bit in order to "dilute" the use of bad addresses over time.

To summarize the principles to be followed when starting up:

* Importing invalid addresses into the quarantine table (if you have this information)
* Limiting the throughput rate (technical setting: limiting the number of mtachilds)
* Progressively increasing the volumes sent: Do not target the whole database from the very start, but rather add an extra fraction of the list each time you send; this should enable you to increase the volume at each step while reducing the overall rate of invalid addresses
* Sending regularly: To a certain extent is better to send small shots regularly than large campaigns sporadically
* Paying close attention to the delivery reports: high error indicators can mean a technical setting is badly configured.