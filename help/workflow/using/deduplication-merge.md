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

For more information on this fonctionality, refer to [this section](../../workflow/using/deduplication.md#merging-fields-into-single-record).

The **[!UICONTROL Deduplication]** activity is used for removing duplicate rows from a data set. In this use case, the data shown below is duplicated based on the Email field. 

|Date | First Name | Last Name | Email | Mobile Phone | Phone|
|-----|------------|-----------|-------|--------------|------|
|5/19/2013 | Robert | Tisner | bob@mycompany.com | | 777-777-7777|
|7/22/2013 | Bobby | | bob@mycompany.com | | 777-777-7777|
|2/3/2013 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888|

With the Deduplication activity's **[!UICONTROL Merge]** fonctionality, you can configure a set of rules for the deduplication to define a group of fields to merge into a single resulting data record. For example, with a set of duplicate records, you can choose to keep the oldest phone number or most recent name.

Here are the rules we want to use to merge the data into a single record:

* Deduplicate on the email field,
* Keep the most recent name (first name and last name fields),
* Keep the most recent mobile phone,
* Keep the oldest phone number,

## Activing the Merge functionality {#activating-merge}

1. Open the **[!UICONTROL Deduplication]** activity, then click the **[Edit configuration]** link.

1. Select the **[!UICONTROL Email]** as reconciliation field for the deduplication, then click **[!UICONTROL Next]**.

    ![](assets/uc_merge_edit.png)

1. Click the **[!UICONTROL Advanced parameters]** link, then activate the **[!UICONTROL Merge records]** and **[!UICONTROL Use several record merging criteria]** options.

    ![](assets/uc_merge_advanced_parameters.png)

1. The **[!UICONTROL Merge]** tab is added to the **[!UICONTROL Deduplication]** configuration screen.

    We will use this tab to specify the data to merge when performing deduplication. To do this, click the **[!UICONTROL Add]** button.

    ![](assets/uc_merge_add.png)

## Configuring the rules {#configuring-rules}

1. Specify the identifier of the group of fields to be merged.

    ![](assets/uc_merge_identifier.png)

1. Indicate the conditions for selecting the records to be taken into account.

    ![](assets/uc_merge_filter.png)

1. Sort on date to select the most recent first name and last name.

    ![](assets/uc_merge_sort.png)

1. Select the fields to merge. In our case, we want to keep the first name, last name, and date.

    ![](assets/uc_merge_keep.png)

1. The rule is added to the set of rules and a new element is added to the workflow schema.

    ![](assets/dedup8.png)
  
    ![](assets/dedup9.png)

## Results {#results}

After configuring these rules, the following data is received at the end of the **[!UICONTROL Deduplication]** activity.

Date | First Name | Last Name | Email | Mobile Phone | Phone
-----|------------|-----------|-------|--------------|------
2/3/2013 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888
5/19/2013 | Robert | Tisner | bob@mycompany.com |   | 777-777-7777
7/22/2013 | Bobby |   | bob@mycompany.com |   | 777-777-7777

The result is merged from the three records according to the rules configured earlier. After comparison, it is concluded that the most recent first name, last name, and mobile phone are used, along with the original phone (Home) used to build the data.

Date | First Name | Last Name | Email | Mobile Phone | Phone
-----|------------|-----------|-------|--------------|------
2/3/2013 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888
