---
title: Using an external recipient table
seo-title: Using an external recipient table
description: Using an external recipient table
seo-description: 
page-status-flag: never-activated
uuid: f1fa2d1e-078b-44ea-9a9f-80212ebf34bf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: a46344b1-d8ed-4fd0-a03d-f26d145f90ab
index: y
internal: n
snippet: y
---

# Using an external recipient table{#using-an-external-recipient-table}

If the delivery table is an external table, you will need to make additional configurations. The **nms:seedmember** schema must be extended. A tab is added to the seed addresses to define the adequate fields, as shown below:

![](assets/s_ncs_user_seedlist_new_tab.png)

In this case, to add seed addresses to the delivery, enter the adequate fields directly in the matching tab, or import the address templates:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

The **nms:seedMember** schema extension is [this section](../../configuration/using/seed-addresses.md).
