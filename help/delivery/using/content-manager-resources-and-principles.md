---
product: campaign
title: Content manager resources and principles
description: Content manager resources and principles
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
---
# Content manager resources and principles{#content-manager-resources-and-principles}

You need to define a publication template, which contains transformation templates for each content.

A content block is structured in an XML document for data storage. An edit interface is used to input the content from the Adobe Campaign client console or via a web browser. The content can also be entered automatically via the capture of XML flow or data aggregated in a database.

Combining the XML document and the XSL or JavaScript Template stylesheets automatically generates the projection of the publication template in the various formats (HTML, text).

![](assets/d_ncs_content_process.png)

The following resources are required for content configuration:

* Data schemas: description of the XML content structure. For more on this, refer to [Data schemas](data-schemas.md).
* Data entry forms: construction of data entry screens. For more on this, refer to [Input forms](input-forms.md).
* Images: images used in data entry forms. For more on this, refer to [Image management](formatting.md#image-management).
* Stylesheets: formatting of output documents using XSLT language. For more on this, refer to [Formatting](formatting.md).
* JavaScript templates: formatting of output documents using JavaScript language. For more on this, refer to [Publication templates](publication-templates.md).
* JavaScript codes: JavaScript codes for data aggregation. For more on this, refer to [Aggregator](publication-templates.md#aggregator).
* Publication templates: definition of publication templates. For more on this, refer to [Publication templates](publication-templates.md).
* Content: content instances to be created and published. For more on this, refer to [Using a content template](using-a-content-template.md).
