---
product: campaign
title: Structure of a data schema
description: Structure of a data schema
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
feature_v2: []
subfeature_v2: []
---
# Structure of a data schema{#structure-of-a-data-schema}

The structure of a data schema is shown in the form of a tree structure. To view it graphically in the Adobe Campaign client console, select the targeted schema and click the **[!UICONTROL Structure]** sub-tab.

![](assets/d_ncs_integration_schema_arbo.png)

As a standard, the fields are displayed first (Active, Activated, etc.) and in alphabetical order. The structuring elements come next (Postal address, Location), and finally the links (Email information, Folder, etc.).

Primary keys are identified by a red key, and foreign keys are identified by a yellow key.

Links are distinguished graphically depending on whether they belong to the table. Those that start from the table, i.e. that have the foreign key in the table, are displayed first (Email information, Folder, Country). "Reverse" collection links (Subscription, Orders, etc.) are displayed at the end.
