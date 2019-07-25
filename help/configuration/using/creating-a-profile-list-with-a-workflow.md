---
title: Creating a profile list with a workflow
seo-title: Creating a profile list with a workflow
description: Creating a profile list with a workflow
seo-description: 
page-status-flag: never-activated
uuid: 3ff70fb3-71db-4dee-b556-48c32f837566
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 7c535ec7-c0d4-4c41-af48-fcc639c233da
index: y
internal: n
snippet: y
---

# Creating a profile list with a workflow{#creating-a-profile-list-with-a-workflow}

To create a **List** type list based on the new recipient table, you need to create a targeting workflow which will generate the list. For more information about lists in Campaign, refer to [this section](/platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Go to the **Profiles and Targets > Jobs > Targeting workflows** node of the explorer.
1. Create a new targeting workflow.
1. Place a **Query** activity followed by a **List update** activity.

   ![](assets/mapping_create_list_workflow01.png)

1. Double-click the **Query** activity, then click **Edit the query** to choose a targeting dimension based on the schema of the new recipient table (in our example: **Individual**). Click **Finish** to confirm.

   ![](assets/mapping_create_list_workflow03.png)

1. Double-click the **List update** activity, then select the **Create the list if necessary (Computed name)** radio button.

   ![](assets/mapping_create_list_workflow02.png)

1. Select the creation folder for the new list.
1. Execute the workflow to create the list.
1. View the result in the node of the tree which you selected during the **List update** activity.

   The dashboard specifies the schema which the list is based on, as shown below:

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>You can also refer to the [Creating a list of recipients](https://helpx.adobe.com/campaign/kt/acc/using/acc-creating-a-list-of-recipients-feature-video-use.html) video.

