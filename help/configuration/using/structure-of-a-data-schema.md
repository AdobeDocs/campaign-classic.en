---
title: Structure of a data schema
seo-title: Structure of a data schema
description: Structure of a data schema
seo-description: 
page-status-flag: never-activated
uuid: b3f3073a-ae90-4401-b7d6-743f75466aae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 43165e91-cc45-471c-94b2-55befe4bbd19
index: y
internal: n
snippet: y
---

# Structure of a data schema{#structure-of-a-data-schema}

The structure of a data schema is shown in the form of a tree structure. To view it graphically in the Adobe Campaign client console, select the targeted schema and click the **Structure** sub-tab.

![](assets/d_ncs_integration_schema_arbo.png)

As a standard, the fields are displayed first (Active, Activated, etc.) and in alphabetical order. The structuring elements come next (Postal address, Location), and finally the links (E-mail information, Folder, etc.).

Primary keys are identified by a red key, and foreign keys are identified by a yellow key.

Links are distinguished graphically depending on whether they belong to the table. Those that start from the table, i.e. that have the foreign key in the table, are displayed first (E-mail information, Folder, Country). "Reverse" collection links (Subscription, Orders, etc.) are displayed at the end.
