---
solution: Campaign Classic
product: campaign
title: Console update
description: Console update
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
---
# Console update{#console-update}

If you selected the **[!UICONTROL Do not request console update]** option and you wish to reactivate the update request, apply the following procedure:

1. Open the editor of the registry database using the **regedit** command in the Windows **[!UICONTROL Start > Execute]** menu.

   ![](assets/ncs_console_update_1.png)

1. In the tree, display the options of the **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** node.
1. Delete the **[!UICONTROL confAdvisedUpgrade]** entry and close the Registry editor.

   ![](assets/ncs_console_update_2.png)
