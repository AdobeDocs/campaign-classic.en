---
solution: Campaign Classic
product: campaign
title: Using MX servers with Campaign
description: Learn how to update bounce qualification after an ISP outage.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: yes
---

# Update bounce qualification after an ISP outage {#update-bounce-qualification.md}

## Context

In case of an outage of an ISP,  emails sent through Campaign cannot be successfully delivered to their recipient: these emails will be wrongly marked as bounces. 

In December 2020, a global issue at Gmail resulted in some email messages sent to valid Gmail email addresses being incorrectly hard bounced as invalid email addresses by Gmail servers with the bounce following response: *“550-5.1.1 The email account that you tried to reach does not exist.”*

Google has stated that the Gmail outages and disruptions that caused this issue started on December 14th at 6:55AM and ended at 6:09PM EST on December 15th. Our data analysis also showed a very short spike in Gmail bounces at 2:06AM EST on December 16th, with the majority occurring on December 15th between 2:00 pm EST and 6:30 pm EST. You can check the Google Workspace Status Dashboard on [this page](https://www.google.com/appsstatus#hl=en&v=status).

Per standard bounce handling logic, Adobe Campaign automatically added these recipients to the Quarantine list with a ‘Status’ setting of ‘Quarantine’. To correct this, you need to update your Quarantine table in Campaign by finding and removing these recipients, or changing their ‘Status’ to ‘Valid’ so that the nightly clean-up workflow will remove them. 

To find the recipients who were affected by this Gmail issue, please see the instructions below.

## Process to update

You will need to run a query on your Quarantine table to filter out all Gmail recipients who were potentially affected by this Gmail outage so they can be removed from the Quarantine list, and included in future Campaign email deliveries.

Based on the timeframe of the incident, below are the recommended guidelines for this query.

>[!IMPORTANT]
>
>These dates/times are based on the Eastern Standard time zone (EST). Please adjust for your instance’s time zone.

* For Campaign instances with SMTP bounce response information in the **Error text** field in the Quarantine list:

    * Error text (quarantine text) contains “550-5.1.1 The email account that you tried to reach does not exist” AND Error text (quarantine text) contains “support.google.com” **
    * Update status (@lastModified) on or after 12/14/2020 6:55:00 AM  
    * Update status (@lastModified) on or before 12/16/2020 6:00:00 AM

* For Campaign Classic instances with Inbound Email rule information in the **Error text** field in the Quarantine list:

    * Error text (quarantine text) contains “Momen_Code10_InvalidRecipient”
    * Email domain (@domain) equal to “gmail.com” OR Email domain (@domain) equal to “googlemail.com”
    * Update status (@lastModified) on or after 12/14/2020 6:55:00 AM  
    * Update status (@lastModified) on or before 12/16/2020 6:00:00 AM

Once you have the list of affected recipients, you can either set them to a status of Valid so they will be removed from the Quarantine list by the Database cleanup workflow, or just delete them from the table.

**Related topics:**
* Understand delivery failures in Campaign Standard
* Understand delivery failures in Campaign Classic

