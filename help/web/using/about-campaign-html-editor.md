---
title: About Campaign HTML editor
seo-title: About Campaign HTML editor
description: About Campaign HTML editor
seo-description: 
page-status-flag: never-activated
uuid: 01d36133-99be-4333-851f-ebca6403eef3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 75b45085-d600-4e97-8a41-6d7c229a4dc3
index: y
internal: n
snippet: y
---

# About Campaign HTML editor{#about-campaign-html-editor}

The **Digital Content Editor (DCE)** is an HTML content editor that lets you easily create or modify templates or content in HTML format within Adobe Campaign.

The Digital Content Editor allows you to insert and format page elements and associate database fields with elements of an HTML page. It is offered by default when creating a page for a Web application, or available when creating deliveries based on a template in which it is active.

>[!NOTE]
>
>The DCE only allows you to carry out the operations detailed in this section.  
>If you would like to add server-side JavaScript code, it is better to add it in personalization blocks. For more information on creating and modifying personalization blocks, refer to [this page](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>For privacy reasons, we recommend to use HTTPS for all external resources.

## Content Editor general operation {#content-editor-general-operation}

This section presents the main steps to edit and upload content edited with the DCE within the framework of a Web application and in the context of a delivery.

The general operation is as follows: 

![](assets/dce_schema.png)

To create a Web application, the steps are as follows:

* Creating a 'Landing page' type Web application, for more on this, refer to [Creating a landing page](../../web/using/creating-a-landing-page.md),
* Selecting existing content or creating content from a standard template, for more on this, refer to [Template management](../../web/using/template-management.md),
* Editing and configuring online content, for more on this, refer to [Editing content](../../web/using/editing-content.md),
* Publishing the Web application, for more on this, refer to [Step 3 - Publishing content](../../web/using/about-campaign-html-editor.md#step-3---publishing-content) and [this page](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of a Web application, refer to [Creating a landing page](../../web/using/creating-a-landing-page.md).

To create an email delivery, the steps are as follows:

* Creating a delivery from an email type template in which the DCE is active,
* Selecting existing content or creating content from a standard template,
* Editing and configuring online content,
* Sending the delivery, for more on this refer to the [this section](../../delivery/using/communication-channels.md).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of an email delivery, refer to [Use case: creating an email delivery](../../web/using/use-case--creating-an-email-delivery.md).

