---
title: Using an external recipient table
seo-title: Using an external recipient table
description: Using an external recipient table
seo-description: 
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
index: y
internal: n
snippet: y
---

# Using an external recipient table{#using-an-external-recipient-table}

If the delivery table is an external table, you will need to make additional configurations. The **[!UICONTROL nms:seedmember]** schema must be extended. A tab is added to the seed addresses to define the adequate fields, as shown below:

![](assets/s_ncs_user_seedlist_new_tab.png)

In this case, to add seed addresses to the delivery, enter the adequate fields directly in the matching tab, or import the address templates:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

The **nms:seedMember** schema extension is [this section](https://helpx.adobe.com/campaign/classic/configuration/using/seed-addresses.html).
