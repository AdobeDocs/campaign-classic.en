---
product: campaign
title: Update bounce qualification after Apple 2021 outage
description: Learn how to update bounce qualification after Apple 2021 outage
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
TQID: https://experienceleague.adobe.com/kn5H0jxM7KKnLGQ3vYdvhQm4nixgSTVhFBO8CAh-1Lg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer (Campaign)
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages (Campaign)
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging (Campaign)
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design (Campaign)
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing (Campaign)
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability (Campaign)
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
>These dates/times are based on the Eastern Standard time zone (EST). Please adjust for your instance's time zone.

* For Campaign instances with SMTP bounce response information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains "user lookup success but no user record found" AND **Error text (quarantine text)** contains "support.apple.com"
    * **Update status (@lastModified)** on or after 4/26/2021 07:00:00 AM  
    * **Update status (@lastModified)** on or before 4/26/2021 01:00:00 PM

* For Campaign instances with Inbound Email rule information in the **[!UICONTROL Error text]** field of the quarantine list:

    * **Error text (quarantine text)** contains "Momen_Code10_InvalidRecipient"
    * **Email domain (@domain)** equal to icloud.com OR **Email domain (@domain)** equal to me.com OR **Email domain (@domain)** equal to mac.com
    * **Update status (@lastModified)** on or after 4/26/2021 07:00:00 AM   
    * **Update status (@lastModified)** on or before 4/26/2021 01:00:00 PM

Once you have the list of affected recipients, you can either set them to a status of **[!UICONTROL Valid]** so they will be removed from the quarantine list by the **[!UICONTROL Database cleanup]** workflow, or just delete them from the table.

**Related topics:**
* [Understand Delivery Failures](delivery-failures-quarantine.md)
* [Bounce mail qualification](delivery-failures-quarantine.md#bounce-mail-qualification)
