---
title: Using the Deduplication activity's Merge functionality
description: Learn how to use the Deduplication activity's Merge functionality
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
---

# Using the Deduplication activity's Merge functionality {#deduplication-merge}

## About this use case {#about-this-use-case}

This use case describes how to use of the **[!UICONTROL Merge]** functionality in the **[!UICONTROL Deduplication]** activity.

The data shown below is duplicated based on the **[!UICONTROL Email]** field.

Date | First Name | Last Name | Email | Mobile Phone | Phone
-----|------------|-----------|-------|--------------|------
2/3/2013 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888
5/19/2013 | Robert | Tisner | bob@mycompany.com |   | 777-777-7777
7/22/2013 | Bobby |   | bob@mycompany.com |   | 777-777-7777

Here are the rules we want to use to merge the data into a single record:

* Deduplicate on the email field,
* Keep the most recent name (first name and last name fields),
* Keep the most recent mobile phone,
* Keep the oldest phone number,
* All fields in a group must be non-null to be eligible for the final record.

## Configuring the rules {#configuring-rules}

1. Open the **[!UICONTROL Deduplication]** activity, then click the **[Edit configuration]** link.

1. Keep the most recent name (first name and last name).

1. Indicate the identifier of the group of fields to be merged.

  ![](assets/dedup4.png)

1. Indicate the conditions for selecting the records to be taken into account.

  ![](assets/dedup5.png)

1. Sort on date to select most recent first and the last name.

  ![](assets/dedup6.png)

1. Select the data to be merged.

  ![](assets/dedup7.png)

1. This rule is then added to the set of rules and a new element is added to the workflow schema.

  ![](assets/dedup8.png)
  
  ![](assets/dedup9.png)

## Results {#results}

Eventually when the user configures all the rules in the Merge tab, the following data is received at the end of the **[!UICONTROL Deduplication]** activity.

The result is merged from the three records as per the rules defined in the merge functionality. After comparison, it is concluded that the most recent first name, last name, and mobile phone are used, along with the original phone (Home) used to build the data.

**Original data**

Date | First Name | Last Name | Email | Mobile Phone | Phone
-----|------------|-----------|-------|--------------|------
2/3/2013 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888
5/19/2013 | Robert | Tisner | bob@mycompany.com |   | 777-777-7777
7/22/2013 | Bobby |   | bob@mycompany.com |   | 777-777-7777

**Result from the **[!UICONTROL Merge]** functionality**

Date | First Name | Last Name | Email | Mobile Phone | Phone
-----|------------|-----------|-------|--------------|------
2/3/2013 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888

**Related topics:**

* Deduplication activity in Campaign Classic
* Targetting data
* Workflow best practices
* Importing profiles
