---
product: campaign
title: Update bounce qualification after an ISP outage
description: Learn how to update bounce qualification after an ISP outage
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
---
# Update incorrect hard bounces after an ISP outage {#update-bounce-qualification}

![](../../assets/common.svg)

## Context{#update-bounce-context}

In case of an outage of an ISP, emails sent through Campaign cannot be successfully delivered to their recipient: these emails will be wrongly marked as bounces.

Global issues at Apple or Gmail for example can result in some email messages sent to valid Apple or Gmail email addresses being incorrectly hard bounced as invalid email addresses by the ISP servers with the bounce following responses:

*  "550 5.1.1 'email address': user lookup success but no user record found."

* “550 'email address' recipient rejected” 

Note that if deferral bounces with the message “452 requested action aborted: try again later” are being observed – these are automatically retried, and no actions are needed. They should improve as the ISP recovers full capacity.

## Symptoms{#update-bounce-symptoms}

In case of an outage of an ISP, emails sent through Campaign cannot be successfully delivered to their recipient: these emails will be wrongly marked as bounces.

Per standard bounce handling logic, Adobe Campaign automatically added these recipients to the quarantine list with a **[!UICONTROL Status]** setting of **[!UICONTROL Quarantine]**. To correct this, you need to update your quarantine table in Campaign by finding and removing these recipients, or changing their **[!UICONTROL Status]** to **[!UICONTROL Valid]** so that the nightly clean-up workflow will remove them. 

To find the recipients who were affected by this issue, see the instructions below.

## Process to update{#update-bounce-update}

You need to run a query on your quarantine table to filter out all impacted recipients - for example for Apple, the addresses which include, @icloud.com, @me.com, @mac.com - who were potentially affected by the outage so they can be removed from the quarantine list, and included in future Campaign email deliveries.

Based on the timeframe of the incident, below are the recommended guidelines for this query.

* For Campaign instances with SMTP bounce response information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains “user lookup success but no user record found” AND **Error text (quarantine text)** contains “support.apple.com”
    * **Update status (@lastModified)** on or after MM/DD/YYYY HH:MM:SS AM
    * **Update status (@lastModified)** on or before  MM/DD/YYYY HH:MM:SS PM

* For Campaign instances with Inbound Email rule information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains “Momen_Code10_InvalidRecipient”
    * **Email domain (@domain)** equal to domain1.com OR **Email domain (@domain)** equal to domain2.com OR **Email domain (@domain)** equal to domain3.com
    * **Update status (@lastModified)** on or after MM/DD/YYYY HH:MM:SS AM
    * **Update status (@lastModified)** on or before MM/DD/YYYY HH:MM:SS PM

Once you have the list of affected recipients, you can either set them to a status of **[!UICONTROL Valid]** so they will be removed from the quarantine list by the **[!UICONTROL Database cleanup]** workflow, or just delete them from the table.

**Related topics:**
* [Understand Delivery Failures](understanding-delivery-failures.md)
* [Bounce mail qualification](understanding-delivery-failures.md#bounce-mail-qualification)
