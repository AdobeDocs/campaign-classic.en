---
title: Managing profiles
seo-title: Managing profiles
description: Managing profiles
seo-description: 
page-status-flag: never-activated
uuid: f045dd5e-e069-4293-8c44-49d71071b041
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: ef7aa3a0-249f-46eb-9300-5b97bce31c8c
---

# Managing profiles{#managing-profiles}

## Recipient tree {#recipient-tree}

To access the advanced recipient management functionalities, you need to edit the Adobe Campaign tree. To do this, click the **[!UICONTROL Explorer]** button in the toolbar.

By default, recipients are stored in the **[!UICONTROL Profiles and targets]** node of the Adobe Campaign tree. From the same node, you can create one or more folders and sub-folders to store recipient profiles.

Each node coincides with a folder. The data from each folder must be considered to be partitioned from each other. This means that the management of doubles will be trickier for multiple recipient folders.

>[!NOTE]
>
>To display the list of all recipients in the database, you must create a view. Refer to [Folders and views](../../platform/using/access-management.md#folders-and-views).

## Moving recipients {#moving-recipients}

You can select one or more recipients, drag them from the recipient list, and drop them in the desired folder. A warning message asks you to confirm this action.

## Copying a recipient {#copying-a-recipient}

You can copy a recipient in the same folder by right-clicking the desired recipient and selecting **[!UICONTROL Copy]**.

## Deleting recipients {#deleting-recipients}

To delete recipients, move them to a specific folder and then purge the content of this folder. It is **strongly recommended not to use** the **[!UICONTROL Delete]** option in this case.

To purge a folder, use the **[!UICONTROL Actions > Purge folder]** menu, accessed by right-clicking the desired folder.

![](assets/s_ncs_user_purge_folder.png)

Click **[!UICONTROL Start]** to launch the operation. The middle section of the window displays the progress status, as shown below:

![](assets/s_ncs_user_purge_folder_start.png)

