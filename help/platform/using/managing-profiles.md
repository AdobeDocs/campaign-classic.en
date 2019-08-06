---
title: Managing profiles
seo-title: Managing profiles
description: Managing profiles
seo-description: 
page-status-flag: never-activated
uuid: ce9c9509-19fe-4e97-b83d-a2d0e3f3ab92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 365c89ec-2c67-430d-9264-30b483cd6e0b
index: y
internal: n
snippet: y
---

# Managing profiles{#managing-profiles}

## Recipient tree {#recipient-tree}

To access the advanced recipient management functionalities, you need to edit the Adobe Campaign tree. To do this, click the **Explorer** button in the toolbar.

By default, recipients are stored in the **Profiles and targets** node of the Adobe Campaign tree. From the same node, you can create one or more folders and sub-folders to store recipient profiles.

Each node coincides with a folder. The data from each folder must be considered to be partitioned from each other. This means that the management of doubles will be trickier for multiple recipient folders.

>[!NOTE]
>
>To display the list of all recipients in the database, you must create a view. Refer to [Folders and views](../../platform/using/managing-profiles.md#folders-and-views).

## Moving recipients {#moving-recipients}

You can select one or more recipients, drag them from the recipient list, and drop them in the desired folder. A warning message asks you to confirm this action.

## Copying a recipient {#copying-a-recipient}

You can copy a recipient in the same folder by right-clicking the desired recipient and selecting **Copy**.

## Deleting recipients {#deleting-recipients}

To delete recipients, move them to a specific folder and then purge the content of this folder. It is **strongly recommended not to use** the **Delete** option in this case.

To purge a folder, use the **Actions > Purge folder** menu, accessed by right-clicking the desired folder.

![](assets/s_ncs_user_purge_folder.png)

Click **Start** to launch the operation. The middle section of the window displays the progress status, as shown below:

![](assets/s_ncs_user_purge_folder_start.png)

