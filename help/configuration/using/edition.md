---
product: campaign
title: Edit Campaign Explorer navigation tree
description: Edit Campaign Explorer navigation tree
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
TQID: https://experienceleague.adobe.com/k8LhZvPSYchAxnQew5eknkDbxHDznzPefl032auuYLc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Edit Campaign Explorer navigation tree{#edition}

The screen for creating and configuring the navigation hierarchy configuration documents is accessible via the **[!UICONTROL Administration > Configuration > Navigation hierarchies]** node:

![](assets/d_ncs_integration_navigation_arbo.png)

The navigation hierarchy configuration is divided over several XML documents. It operates on a similar principle to schema extension: all documents are merged to generate a single document containing the whole configuration. This document cannot be edited, and is displayed via the "Preview" tab.

The edit field provides the content of the XML document:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>The "Name" edit control lets you enter the document key consisting of the name and namespace. The "name" and "namespace" attributes of the **`<navtree>`** element are automatically updated in the XML edit field of the schema.

The preview automatically generates the merged document containing the complete configuration:

![](assets/d_ncs_integration_navigation_preview.png)
