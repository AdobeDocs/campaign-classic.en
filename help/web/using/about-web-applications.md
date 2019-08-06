---
title: About web applications
seo-title: About web applications
description: About web applications
seo-description: 
page-status-flag: never-activated
uuid: 0fad0f48-4c0d-413b-ab3d-7ceabff75e9c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: acbea58e-3bf2-46f4-a5d5-58108a759e3f
index: y
internal: n
snippet: y
---

# About web applications{#about-web-applications}

Adobe Campaign lets you create and publish dynamic and interactive Web applications with data from the database and content adapted to the rights of the connected user. You can create pages, such as an edit form on an extranet, or notification forms including data from the database with tables, charts, input forms, etc. This functionality lets you design and post Web pages where users can look up or enter information.

This can be a subscription form containing data that has been preloaded with information contained in the Adobe Campaign database, as shown below:

![](assets/webapp_form_sample.png)

This chapter provides an overview of how to manage Web applications.

>[!CAUTION]
>
>For privacy reasons, we recommend to use HTTPS for all external resources.

## Web application scope {#web-application-scope}

Web applications in Adobe Campaign give access to the following capabilities:

* Multiple-page form creation,
* Multilingual survey management with an integrated translation tool,
* Graphical page management interface, multiple-column page layout,
* Rendering personalization and field position,
* Conditional display of survey fields according to answers,
* Random display of questions,
* Conditional page display,
* Information check before validation depending on the expected data type (number, e-mail address, date, etc.) and the mandatory fields,
* E-mail invitations or notification,
* Personalization of error and end messages,
* Use of images, videos, hypertext links, captcha, etc.
* Monitoring of responses in real time.

The optional survey creation module (**Survey**) offers the following additional functionalities:

* Dynamic extension of the database: creation of responses not included in the initial data template,
* Generating dedicated reports.

Compared to Web applications, surveys have a simplified graphical interface with a reduced number of editing controls.

>[!NOTE]
>
>Surveys are detailed in [this section](../../web/using/about-surveys.md).  
>The overall functionalities of Web forms in Adobe Campaign are detailed in [this section](../../web/using/about-web-forms.md).

## Web application implementation {#web-application-implementation}

To create and post a Web application, you must:

1. Create the content (fields, lists, tables, graphs, etc.).

   You can also view the section which details the available fields for forms: all these fields are also available for Web applications. This information is available in [this page](../../web/using/adding-fields-to-a-web-form.md).

1. As required, you can add preloading, test, and saving steps, and configure the access control system (mainly within the framework of an extranet publication).
1. Publishing the Web application to make it available on an extranet or in Adobe Campaign.

## Web application initial configuration {#web-application-initial-configuration}

Web application are created via the **Web Applications** link in the **Campaigns** and **Profiles and targets** tabs.

Web applications are stored in the **Resources > Online > Web Applications** node of the Adobe Campaign tree. Configurations are broken down in the following folders:

* **Administration > Configuration > Form renderings**: contains the rendering templates for the Web form presentation (applications and surveys). The template enables you to generate the form. It also uses a CSS style sheet. This style sheet can be overloaded at the template level. For more on this, refer to [this page](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **Resources > Templates > Web application templates**: contains form templates. To create a form or a Web application, you must start from a template.

## Web application templates {#web-application-templates}

By default, Adobe Campaign provides one template per available Web application.

>[!NOTE]
>
>You can convert an existing Web application into a template. To do this, select the form and right-click. Select **Actions > Save as template...**.

You can create new templates via the **Resources > Templates > Web Application templates** node of the Adobe Campaign tree.

The creation wizard lets you select the options you want to enable, as shown below. 

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>The available applications depend on your options and modules. Please check your license agreement.

