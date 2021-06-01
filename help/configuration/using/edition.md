---
product: campaign
title: Edition
description: Edition
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
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
