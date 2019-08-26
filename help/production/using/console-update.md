---
title: Console update
seo-title: Console update
description: Console update
seo-description: 
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
index: y
internal: n
snippet: y
---

# Console update{#console-update}

If you selected the **[!UICONTROL Do not request console update]** option and you wish to reactivate the update request, apply the following procedure:

1. Open the editor of the registry database using the **regedit** command in the Windows **[!UICONTROL Start > Execute]** menu.

   ![](assets/ncs_console_update_1.png)

1. In the tree, display the options of the **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** node.
1. Delete the **[!UICONTROL confAdvisedUpgrade]** entry and close the Registry editor.

   ![](assets/ncs_console_update_2.png)

