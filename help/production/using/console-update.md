---
product: campaign
title: Console update
description: Console update
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring (Campaign)
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines (Campaign)
---
# Console update{#console-update}



If you selected the **[!UICONTROL Do not request console update]** option and you wish to reactivate the update request, apply the following procedure:

1. Open the editor of the registry database using the **regedit** command in the Windows **[!UICONTROL Start > Execute]** menu.

   ![](assets/ncs_console_update_1.png)

1. In the tree, display the options of the **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** node.
1. Delete the **[!UICONTROL confAdvisedUpgrade]** entry and close the Registry editor.

   ![](assets/ncs_console_update_2.png)
