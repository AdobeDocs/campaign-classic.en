---
title: Console update
seo-title: Console update
description: Console update
seo-description: 
page-status-flag: never-activated
uuid: ba249f37-653d-4b90-945f-20f884f02b43
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 59713b8a-f02a-4235-9564-02c30f90fb96
index: y
internal: n
snippet: y
---

# Console update{#console-update}

If you selected the **Do not request console update** option and you wish to reactivate the update request, apply the following procedure:

1. Open the editor of the registry database using the **regedit** command in the Windows **Start > Execute** menu.

   ![](assets/ncs_console_update_1.png)

1. In the tree, display the options of the ** HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient** node.
1. Delete the **confAdvisedUpgrade** entry and close the Registry editor.

   ![](assets/ncs_console_update_2.png)

