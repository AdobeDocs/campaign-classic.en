---
product: campaign
title: Use an external recipient table
description: Use an external recipient table
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
TQID: https://experienceleague.adobe.com/Uq5yqNYkyDrFVtueUlkIOEC9XEUaYtBArNy8-t1rKAw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
---
# Use an external recipient table{#using-an-external-recipient-table}

 

If the delivery table is an external table, you will need to make additional configurations. The **[!UICONTROL nms:seedmember]** schema must be extended. A tab is added to the seed addresses to define the adequate fields, as shown below:

![](assets/s_ncs_user_seedlist_new_tab.png)

In this case, to add seed addresses to the delivery, enter the adequate fields directly in the matching tab, or import the address templates:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

The **nms:seedMember** schema extension is [this section](../../configuration/using/seed-addresses.md).
