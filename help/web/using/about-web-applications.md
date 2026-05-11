---
product: campaign
title: Get started with web applications
description: Create and share dynamic Web applications, landing pages and surveys
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
TQID: https://experienceleague.adobe.com/GP-1vCAYzcgjaOyUs-Zkx6rXOLSNbpF7962OEMsw5YM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
  - id: fb2a841f-c522-491f-9901-a1b939d252df
    internal-label: Security
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Get started with web applications{#about-web-applications}

 

Adobe Campaign lets you create and publish dynamic and interactive Web applications with data from the database and content adapted to the rights of the connected user. 

You can create pages, such as an edit form on an extranet, or notification forms including data from the database with tables, charts, input forms, etc. This functionality lets you design and post Web pages where users can look up or enter information.

This can be a subscription form containing data that has been preloaded with information contained in the Adobe Campaign database, as shown below:

   ![](assets/webapp_form_sample.png)

This chapter provides an overview of how to manage Web applications.

>[!NOTE]
>
>Refer to the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html) to learn how to optimize security for web applications.

>[!CAUTION]
>
>For privacy reasons, we recommend to use HTTPS for all external resources.

## Web application scope {#web-application-scope}

Web applications in Adobe Campaign give access to the following capabilities:

* Multiple-page form creation. For more on this, refer to this [page](about-web-forms.md).
* Multilingual survey management with an integrated translation tool. For more on this, refer to this [page](translating-a-web-application.md).
* Graphical page management interface, multiple-column page layout. For more on this, refer to this [page](designing-a-web-application.md).
* Rendering personalization and field position. For more on this, refer to this [page](editing-content.md#adding-personalization-content).
* Conditional display of survey fields according to answers. For more on this, refer to this [page](form-rendering.md#defining-fields-conditional-display).
* Random display of questions. For more on this, refer to this [page](../../surveys/using/building-a-survey.md#adding-questions).
* Conditional page display. For more on this, refer to this [page](defining-web-forms-page-sequencing.md#conditional-page-display).
* Information check before validation depending on the expected data type (number, email address, date, etc.) and the mandatory fields. For more on this, refer to this [page](form-rendering.md#defining-control-settings).
* Email invitations or notification. For more on this, refer to this [page](publishing-a-web-form.md#delivering-a-form-via-email).
* Personalization of error and end messages. For more on this, refer to this [page](defining-web-forms-properties.md#setting-up-an-error-page).
* Use of images, videos, hypertext links, captcha, etc. For more on this, refer to this [page](editing-content.md).
* Monitoring of responses in real time. For more on this, refer to this [page](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).

The optional **Survey** creation module offers the following additional functionalities:

* Dynamic extension of the database: creation of responses not included in the initial data template. For more on this, refer to this [page](../../surveys/using/managing-answers.md#storing-collected-answers).
* Generating dedicated reports. For more on this, refer to this [page](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).

Compared to Web applications, surveys have a simplified graphical interface with a reduced number of editing controls.

>[!NOTE]
>
>Surveys are detailed in [this section](../../surveys/using/about-surveys.md).
>
>The overall functionalities of Web forms in Adobe Campaign are detailed in [this section](about-web-forms.md).

## Web application implementation {#web-application-implementation}

To create and post a Web application, you must:

1. Create the content (fields, lists, tables, graphs, etc.).

   You can also view the section which details the available fields for forms: all these fields are also available for Web applications. This information is available in [this page](adding-fields-to-a-web-form.md).

1. As required, you can add preloading, test, and saving steps, and configure the access control system (mainly within the framework of an extranet publication).
1. Publishing the Web application to make it available on an extranet or in Adobe Campaign.

## Web application initial configuration {#web-application-initial-configuration}

Web application are created via the **[!UICONTROL Web Applications]** link in the **[!UICONTROL Campaigns]** and **[!UICONTROL Profiles and targets]** tabs.

Web applications are stored in the **[!UICONTROL Resources > Online > Web Applications]** node of the Adobe Campaign tree. Configurations are broken down in the following folders:

* **[!UICONTROL Administration > Configuration > Form renderings]**: contains the rendering templates for the Web form presentation (applications and surveys). The template enables you to generate the form. It also uses a CSS style sheet. This style sheet can be overloaded at the template level. For more on this, refer to [this page](form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: contains form templates. To create a form or a Web application, you must start from a template.

## Web application templates {#web-application-templates}

By default, Adobe Campaign provides one template per available Web application.

>[!NOTE]
>
>You can convert an existing Web application into a template. To do this, select the form and right-click. Select **[!UICONTROL Actions > Save as template...]**.

You can create new templates via the **[!UICONTROL Resources > Templates > Web Application templates]** node of the Adobe Campaign tree.

The creation assistant lets you select the options you want to enable, as shown below. 

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>The available applications depend on your options and modules. Please check your license agreement.
