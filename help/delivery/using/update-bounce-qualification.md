---
solution: Campaign Classic
product: campaign
title: Update bounce qualification after an ISP outage
description: Learn how to update bounce qualification after an ISP outage.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: yes
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
---
# Update bounce qualification after an ISP outage {#update-bounce-qualification.md}

## Context

In case of an outage of an ISP, emails sent through Campaign cannot be successfully delivered to their recipient: these emails will be wrongly marked as bounces.

In December 2020, a global issue at Gmail resulted in some email messages sent to valid Gmail email addresses being incorrectly hard bounced as invalid email addresses by Gmail servers with the bounce following response: *“550-5.1.1 The email account that you tried to reach does not exist.”*

Google has stated that the Gmail outages and disruptions that caused this issue started on December 14th at 6:55AM and ended at 6:09PM EST on December 15th. Our data analysis also showed a very short spike in Gmail bounces at 2:06AM EST on December 16th, with the majority occurring on December 15th between 2:00 pm EST and 6:30 pm EST.

>[!NOTE]
>
>You can check the Google Workspace Status Dashboard on [this page](https://www.google.com/appsstatus#hl=en&v=status).


Per standard bounce handling logic, Adobe Campaign automatically added these recipients to the quarantine list with a **[!UICONTROL Status]** setting of **[!UICONTROL Quarantine]**. To correct this, you need to update your quarantine table in Campaign by finding and removing these recipients, or changing their **[!UICONTROL Status]** to **[!UICONTROL Valid]** so that the nightly clean-up workflow will remove them. 

To find the recipients who were affected by this Gmail issue, or in case this happens again with any other ISP, please see the instructions below.

## Process to update

You will need to run a query on your quarantine table to filter out all Gmail (or other ISP) recipients who were potentially affected by the outage so they can be removed from the quarantine list, and included in future Campaign email deliveries.

Based on the timeframe of the incident, below are the recommended guidelines for this query.

>[!IMPORTANT]
>
>These dates/times are based on the Eastern Standard time zone (EST). Please adjust for your instance’s time zone.

* For Campaign instances with SMTP bounce response information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains “550-5.1.1 The email account that you tried to reach does not exist” AND **Error text (quarantine text)** contains “support.google.com” **
    * **Update status (@lastModified)** on or after 12/14/2020 6:55:00 AM  
    * **Update status (@lastModified)** on or before 12/16/2020 6:00:00 AM

* For Campaign instances with Inbound Email rule information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains “Momen_Code10_InvalidRecipient”
    * **Email domain (@domain)** equal to “gmail.com” OR Email domain (@domain) equal to “googlemail.com”
    * **Update status (@lastModified)** on or after 12/14/2020 6:55:00 AM  
    * **Update status (@lastModified)** on or before 12/16/2020 6:00:00 AM

Once you have the list of affected recipients, you can either set them to a status of **[!UICONTROL Valid]** so they will be removed from the quarantine list by the **[!UICONTROL Database cleanup]** workflow, or just delete them from the table.

**Related topics:**
* [Understand Delivery Failures](../../delivery/using/understanding-delivery-failures.md)
* [Bounce mail qualification](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
