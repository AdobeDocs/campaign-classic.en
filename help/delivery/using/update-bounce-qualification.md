---
product: campaign
title: Update bounce qualification after an ISP outage
description: Learn how to update bounce qualification after an ISP outage.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: yes
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
---
# Update incorrect hard bounces after Apple outage {#update-bounce-qualification.md}

## Context

On April 26 2021, a global issue at Apple resulted in some email messages sent to valid Apple email addresses being incorrectly hard bounced as invalid email addresses by Apple servers with the bounce following response:  "550 5.1.1 'email address': user lookup success but no user record found."

This issue occurred on 4/26 and lasted 7AM - 1PM EST. 

>[!NOTE]
>
>You can check the Apple System Status Dashboard on [this page](https://www.apple.com/support/systemstatus/).

In case of an outage of an ISP, emails sent through Campaign cannot be successfully delivered to their recipient: these emails will be wrongly marked as bounces.

Per standard bounce handling logic, Adobe Campaign automatically added these recipients to the quarantine list with a **[!UICONTROL Status]** setting of **[!UICONTROL Quarantine]**. To correct this, you need to update your quarantine table in Campaign by finding and removing these recipients, or changing their **[!UICONTROL Status]** to **[!UICONTROL Valid]** so that the nightly clean-up workflow will remove them. 

To find the recipients who were affected by this issue, or in case this happens again with any other ISP, please see the instructions below.

## Process to update

You will need to run a query on your quarantine table to filter out all Apple recipients - which includes, @icloud.com, @me.com, @mac.com - who were potentially affected by the outage so they can be removed from the quarantine list, and included in future Campaign email deliveries.

Based on the timeframe of the incident, below are the recommended guidelines for this query.

>[!IMPORTANT]
>
>These dates/times are based on the Eastern Standard time zone (EST). Please adjust for your instance’s time zone.

* For Campaign instances with SMTP bounce response information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains “user lookup success but no user record found” AND **Error text (quarantine text)** contains “support.apple.com”
    * **Update status (@lastModified)** on or after 4/26/2021 07:00:00 AM  
    * **Update status (@lastModified)** on or before 4/26/2021 01:00:00 PM

* For Campaign instances with Inbound Email rule information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains “Momen_Code10_InvalidRecipient”
    * **Email domain (@domain)** equal to icloud.com OR **Email domain (@domain)** equal to me.com OR **Email domain (@domain)** equal to mac.com
    * **Update status (@lastModified)** on or after 4/26/2021 07:00:00 AM   
    * **Update status (@lastModified)** on or before 4/26/2021 01:00:00 PM

Once you have the list of affected recipients, you can either set them to a status of **[!UICONTROL Valid]** so they will be removed from the quarantine list by the **[!UICONTROL Database cleanup]** workflow, or just delete them from the table.

**Related topics:**
* [Understand Delivery Failures](understanding-delivery-failures.md)
* [Bounce mail qualification](understanding-delivery-failures.md#bounce-mail-qualification)
