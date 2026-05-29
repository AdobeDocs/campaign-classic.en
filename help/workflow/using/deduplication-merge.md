---
title: Use the Deduplication activity's Merge functionality
description: Learn how to use the Deduplication activity's Merge functionality
feature: Workflows, Data Management
hide: true
exl-id: a6b10585-7bf9-4fef-b886-db081b6d3acc
TQID: https://experienceleague.adobe.com/1KKmaXm0FnnDnLesz6wayUw25stzk7NfZpcdCQW5Ak4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: Workflow HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
---
# Use the Deduplication activity's Merge functionality {#deduplication-merge}



## About this use case {#about-this-use-case}

This use case describes how to use of the **[!UICONTROL Merge]** functionality in the **[!UICONTROL Deduplication]** activity.

For more information on this functionality, refer to [this section](deduplication.md#merging-fields-into-single-record).

The **[!UICONTROL Deduplication]** activity is used for removing duplicate rows from a data set. In this use case, the data shown below is duplicated based on the Email field. 

|Last modification date | First Name | Last Name | Email | Mobile Phone | Phone|
|-----|------------|-----------|-------|--------------|------|
|5/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777|
|7/22/2020 | Bobby | Tisner | bob@mycompany.com | | 777-777-7777|
|10/03/2020 | Bob |  | bob@mycompany.com | | 888-888-8888|

With the Deduplication activity's **[!UICONTROL Merge]** fonctionality, you can configure a set of rules for the deduplication to define a group of fields to merge into a single resulting data record. For example, with a set of duplicate records, you can choose to keep the oldest phone number or most recent name.

## Activating the Merge functionality {#activating-merge}


To enable the merge functionality, you first need to configure the **[!UICONTROL Deduplication]** activity. To do this, follow these steps:

1. Open the activity, then click the **[Edit configuration]** link.

1. Select the reconciliation field to use for the deduplication, then click **[!UICONTROL Next]**. In this example, we want to deduplicate based on the email field.

    ![](assets/uc_merge_edit.png)

1. Click the **[!UICONTROL Advanced parameters]** link, then activate the **[!UICONTROL Merge records]** and **[!UICONTROL Use several record merging criteria]** options.

    ![](assets/uc_merge_advanced_parameters.png)

1. The **[!UICONTROL Merge]** tab is added to the **[!UICONTROL Deduplication]** configuration screen. We will use this tab to specify the data to merge when performing deduplication.

## Configuring the fields to merge {#configuring-rules}

Here are the rules we want to use to merge the data into a single record:

* Keep the most recent name (first name and last name fields),
* Keep the most recent mobile phone,
* Keep the oldest phone number,
* All fields in a group must be non-null to be eligible for the final record.

To configure these rules, follow these steps:

1. Open the **[!UICONTROL Merge]** tab, then click the **[!UICONTROL Add]** button.

    ![](assets/uc_merge_add.png)

1. Specify the identifier and label of the group of fields to be merged.

    ![](assets/uc_merge_identifier.png)

1. Indicate the conditions for selecting the records to be taken into account.

    ![](assets/uc_merge_filter.png)

1. Sort on the last modification date in order to select the most recent name.

    ![](assets/uc_merge_sort.png)

1. Select the fields to merge. In this example, we want to keep the first name and last name fields.

    ![](assets/uc_merge_keep.png)

1. The fields are added to the set of data to merge and a new element is added to the workflow schema.

    Repeat these steps to configure the mobile phone and phone fields.

    ![](assets/dedup8.png)
  
    ![](assets/dedup9.png)

## Results {#results}

After configuring these rules, the following data is received at the end of the **[!UICONTROL Deduplication]** activity.

| Modification date | First Name | Last Name | Email | Mobile Phone | Phone |
|-----|------------|-----------|-------|--------------|------|
|5/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777|
|7/22/2020 | Bobby | Tisner | bob@mycompany.com | | 777-777-7777|
|10/03/2020 | Bob |  | bob@mycompany.com | | 888-888-8888|

The result is merged from the three records according to the rules configured earlier. After comparison, it is concluded that the most recent name and mobile phone are used, along with the original phone number.

| First Name | Last Name | Email | Mobile Phone | Phone|
|------------|-----------|-------|--------------|------|
| Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888|

>[!NOTE]
>
> Note that the first name that has been merged is "Bobby", because we configured a "Name" rule made of both the first name and last fields.
>
>As a result, "Bob" (the most recent first name) could not be taken into account because its associated last name field was empty. The most recent combination of first and last names was merged in the final record.
