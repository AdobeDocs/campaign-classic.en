---
solution: Campaign Classic
product: campaign
title: Creating a profile list with a workflow
description: Learn how to create a profile list in a workflow
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
---
# Creating a profile list with a workflow{#creating-a-profile-list-with-a-workflow}

To create a **[!UICONTROL List]** type list based on the new recipient table, you need to create a targeting workflow which will generate the list. 

For more information about lists in Campaign, refer to [this section](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

To create a targeting workflow and update recipients in a custom recipient table, follow the steps below: 

1. Go to the **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** node of the explorer.
1. Create a new targeting workflow.
1. Place a **Query** activity followed by a **List update** activity.

   ![](assets/mapping_create_list_workflow01.png)

1. Double-click the **Query** activity, then click **[!UICONTROL Edit the query]** to choose a targeting dimension based on the schema of the new recipient table (in our example: **Individual**). Click **[!UICONTROL Finish]** to confirm.

   ![](assets/mapping_create_list_workflow03.png)

1. Double-click the **List update** activity, then select the **[!UICONTROL Create the list if necessary (Computed name)]** radio button.

   ![](assets/mapping_create_list_workflow02.png)

1. Select the creation folder for the new list.
1. Execute the workflow to create the list.
1. View the result in the node of the tree which you selected during the **[!UICONTROL List update]** activity.

   The dashboard specifies the schema which the list is based on, as shown below:

   ![](assets/mapping_list_view.png)
