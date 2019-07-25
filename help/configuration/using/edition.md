---
title: Edition
seo-title: Edition
description: Edition
seo-description: 
page-status-flag: never-activated
uuid: 434d1109-3d22-4522-8eeb-9233ba2ae7cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 6085d3a7-a195-4d98-a9af-001b825725cb
index: y
internal: n
snippet: y
---

# Edition{#edition}

The screen for creating and configuring the navigation hierarchy configuration documents is accessible via the **Administration > Configuration > Navigation hierarchies** node:

![](assets/d_ncs_integration_navigation_arbo.png)

The navigation hierarchy configuration is divided over several XML documents. It operates on a similar principle to schema extension: all documents are merged to generate a single document containing the whole configuration. This document cannot be edited, and is displayed via the "Preview" tab.

The edit field provides the content of the XML document:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>The "Name" edit control lets you enter the document key consisting of the name and namespace. The "name" and "namespace" attributes of the **`<navtree>`** element are automatically updated in the XML edit field of the schema.

The preview automatically generates the merged document containing the complete configuration:

![](assets/d_ncs_integration_navigation_preview.png)

