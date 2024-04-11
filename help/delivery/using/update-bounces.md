---
product: campaign
title: Update bounce qualification after an ISP outage
description: Learn how to update bounce qualification after an ISP outage
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
hide: yes
hidefromtoc: yes
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
---
# Update incorrect hard bounces after an ISP outage {#update-bounces}

 

## Context{#update-bounce-context}

In case of an outage of an ISP, emails sent through Campaign cannot be successfully delivered to their recipient: these emails will be wrongly marked as bounces.

Global issues at Apple or Gmail for example can result in some email messages sent to valid Apple or Gmail email addresses being incorrectly hard bounced as invalid email addresses by the ISP servers with the bounce following responses:

* "550 5.1.1 'email address': user lookup success but no user record found."

* "550 'email address' recipient rejected" 

Note that if deferral bounces with the message "452 requested action aborted: try again later" are being observed – these are automatically retried, and no actions are needed. They should improve as the ISP recovers full capacity.

>[!NOTE]
>
>You can check the Apple System Status Dashboard on [this page](https://www.apple.com/support/systemstatus/){_blank}.
>
>You can check the Google Workspace Status Dashboard on [this page](https://www.google.com/appsstatus#hl=en&v=status){_blank}.
>

## Impact{#update-bounce-impact}

In case of an outage of an ISP, emails sent through Campaign cannot be successfully delivered to their recipient: these emails will be wrongly marked as bounces.

Per standard bounce handling logic, Adobe Campaign automatically added these recipients to the quarantine list with a **[!UICONTROL Status]** setting of **[!UICONTROL Quarantine]**. To correct this, you need to update your quarantine table in Campaign by finding and removing these recipients, or changing their **[!UICONTROL Status]** to **[!UICONTROL Valid]** so that the nightly clean-up workflow will remove them. 

To find the recipients who were affected by this issue, see the instructions below.

## Process to update{#update-bounce-update}

You need to run a query on your quarantine table to filter out all impacted recipients - for example for Apple, the addresses which include, @icloud.com, @me.com, @mac.com - who were potentially affected by the outage so they can be removed from the quarantine list, and included in future Campaign email deliveries.

Based on the timeframe of the incident, and the ISP, below are the recommended guidelines for this query.

* For Campaign environments with Inbound Email rule information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains "Momen_Code10_InvalidRecipient"
    * **Email domain (@domain)** equal to domain1.com OR **Email domain (@domain)** equal to domain2.com OR **Email domain (@domain)** equal to domain3.com
    * **Update status (@lastModified)** on or after `MM/DD/YYYY HH:MM:SS AM`
    * **Update status (@lastModified)** on or before `MM/DD/YYYY HH:MM:SS PM`

* For Campaign environments with SMTP bounce response information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains "550-5.1.1" AND **Error text (quarantine text)** contains "support.ISP.com" 
        
        where "support.ISP.com" can be: "support.apple.com" or "support.google.com" for example

    * **Update status (@lastModified)** on or after `MM/DD/YYYY HH:MM:SS AM`
    * **Update status (@lastModified)** on or before  `MM/DD/YYYY HH:MM:SS PM`


Once you have the list of affected recipients, you can either set them to a status of **[!UICONTROL Valid]** so they will be removed from the quarantine list by the **[!UICONTROL Database cleanup]** workflow, or just delete them from the table.

**Related topics:**
* [Understand Delivery Failures](understanding-delivery-failures.md)
* [Bounce mail qualification](understanding-delivery-failures.md#bounce-mail-qualification)
