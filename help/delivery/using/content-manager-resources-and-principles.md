---
title: Content manager resources and principles
seo-title: Content manager resources and principles
description: Content manager resources and principles
seo-description: 
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
index: y
internal: n
snippet: y
---

# Content manager resources and principles{#content-manager-resources-and-principles}

You need to define a publication template, which contains transformation templates for each content.

A content block is structured in an XML document for data storage. An edit interface is used to input the content from the Adobe Campaign client console or via a web browser. The content can also be entered automatically via the capture of XML flow or data aggregated in a database.

Combining the XML document and the XSL or JavaScript Template stylesheets automatically generates the projection of the publication template in the various formats (HTML, text).

![](assets/d_ncs_content_process.png)

The following resources are required for content configuration:

* Data schemas: description of the XML content structure. For more on this, refer to [Data schemas](https://helpx.adobe.com/campaign/standard/delivery/using/data-schemas.html).
* Data entry forms: construction of data entry screens. For more on this, refer to [Input forms](https://helpx.adobe.com/campaign/standard/delivery/using/input-forms.html).
* Images: images used in data entry forms. For more on this, refer to [Image management](https://helpx.adobe.com/campaign/standard/delivery/using/formatting.html#image-management).
* Stylesheets: formatting of output documents using XSLT language. For more on this, refer to [Formatting](https://helpx.adobe.com/campaign/standard/delivery/using/formatting.html).
* JavaScript templates: formatting of output documents using JavaScript language. For more on this, refer to [Publication templates](https://helpx.adobe.com/campaign/standard/delivery/using/publication-templates.html).
* JavaScript codes: JavaScript codes for data aggregation. For more on this, refer to [Aggregator](https://helpx.adobe.com/campaign/standard/delivery/using/publication-templates.html#aggregator).
* Publication templates: definition of publication templates. For more on this, refer to [Publication templates](https://helpx.adobe.com/campaign/standard/delivery/using/publication-templates.html).
* Content: content instances to be created and published. For more on this, refer to [Using a content template](https://helpx.adobe.com/campaign/standard/delivery/using/using-a-content-template.html).

