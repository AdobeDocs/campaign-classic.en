---
product: campaign
title: Content manager resources and principles
description: Content manager resources and principle
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
TQID: https://experienceleague.adobe.com/xWBOrnm4v7N3XOVvOcPNqngz0cDvvT39tI3xJVKdFZg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: ce44533e-8ec8-4e11-a9e9-78b0fe561832
    internal-label: Content structure
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
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
