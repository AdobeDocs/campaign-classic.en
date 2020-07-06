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

Maintaining your domain and IP address reputation is essential when setting up a new platform.

* Starting to send emails is a sensitive step because the platform does not have any history of use and, when the sending IPs have never been used for this purpose, no reputation.

* ISPs are naturally suspicious of IP addresses that have never been used to send email and that suddenly start to send large volumes of email traffic. Indeed, spammers generally use "unknown" IP addresses (addresses that have never been added to a block list) to send the largest possible number of messages before detection.

* You cannot expect to reach operational speed in terms of output at the very start of the production phase. Furthermore, you should not attempt to send messages at this rate as it might lead the ISPs to block the sending addresses and to severely compromise the rest of the start-up phase.

Below are listed the main principles to be followed when starting up a new platform:

* If you have this information, **import invalid addresses into the quarantine table**. 
    Starting a platform often happens when using a list of addresses for the first time and which may not be fully qualified. If you send to invalid addresses or to honeypot addresses, this will contribute to diminishing the reputation of the platform.

    * If you have a list of invalid addresses, it is in your best interests to import it into the quarantine table (available through the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** menu) before sending for the first times.
    * If, all the same, you wish to requalify the invalid addresses, it is by far preferable to do this once the reputation of the platform is established and bit by bit in order to "dilute" the use of bad addresses over time.

    For more on this, see [Optimizing your delivery through quarantines](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limit the throughput rate** by limiting the number of mtachilds. For more on adjusting such technical setting, contact your Adobe Campaign administrator.
* **Progressively increase the volumes sent** to avoid being marked as spam. Do not target the whole database from the very start, but rather add an extra fraction of the list each time you send. This should enable you to increase the volume at each step while reducing the overall rate of invalid addresses. To ensure smooth development of the start-up phase, you can use waves. For more on this, see [Sending using multiple waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Send regularly**. To a certain extent it is better to send small shots regularly rather than large campaigns sporadically.
* **Pay close attention to the delivery reports**. High error indicators can mean a technical setting is badly configured. For more on this, see [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).

**Related topics**:
* [Increase your email reputation with IP warming](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [All about Spam traps](https://helpx.adobe.com/campaign/kb/spam-traps.html)