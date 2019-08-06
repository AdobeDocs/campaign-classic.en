---
title: Edition
seo-title: Edition
description: Edition
seo-description: 
page-status-flag: never-activated
uuid: 2cae259f-a710-419a-afee-2fbc975d61f5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: cef2b8e4-232d-456d-9bea-b4a43e4e90dd
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

