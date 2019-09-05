---
title: Blacklisting databases
seo-title: Blacklisting databases
description: Blacklisting databases
seo-description: 
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
index: y
internal: n
snippet: y
---

# Blacklisting databases{#blacklisting-databases}

Several organizations maintain databases of IP addresses and domains that are reputed to be used by spammers. Consulting these sites can be useful to understand why certain messages were rejected as spam. It is generally possible to request the removal of an address erroneously added to these lists.

These databases are called RBLs (Real-time Blackhole Lists) and they are consulted via a DNS mechanism. There are three types of RBLs:

* By IP address: lists IP addresses sending spam or likely to be relaying spam.
* By sender domain: lists sender domains (full domain of the bounce mail address) sending spam or incorrectly configured.
* By web domain: lists the domains (high-level domains as registered with the registrars) found in the URLs of the links and images contained in spam content. In Adobe Campaign, the domain to be taken into consideration is generally the address used for tracking.

The following is a list of the most widely used RBLs. For a more comprehensive list, you can refer to [https://www.declude.com/Articles.asp?ID=97](https://www.declude.com/Articles.asp?ID=97) or [https://www.dnsstuff.com/](https://www.dnsstuff.com/) ("IP Tools" section, "Spam Database Lookup" form).

* Spamhaus

  Refer to [https://www.spamhaus.org/](https://www.spamhaus.org/)

  The database is more important. Being classified on this list is generally a serious situation. If this happens, you must act IMMEDIATELY and warn commercial services, deliverability, and Adobe Campaign support. 

* SpamCop

  Refer to [https://www.spamcop.net/](https://www.spamcop.net/)

  It is one of the most renowned databases. If one of your IP addresses is placed on this list, this generally means that the SpamCop users have declared your messages as being Spam or that you have sent messages to a SpamCop honeypot.

* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.

* URIBL

  Refer to [https://www.uribl.com/](https://www.uribl.com/)

  This list identifies the domains that regularly appear in messages declared as spam. If your domain appears on this list, it can significantly affect your deliverability. You should inform the deliverability services and Adobe Campaign support immediately.

* iX Manitu

  This is a list of IPs and is widely used in Germany. Refer to [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

* SURBL

  Refer to [https://www.surbl.org/](https://www.surbl.org/)

  SURBL identifies the websites that regularly appear in spam. If your domain appears on this list, it can significantly affect your deliverability. You should inform the deliverability services and Adobe Campaign support immediately.
