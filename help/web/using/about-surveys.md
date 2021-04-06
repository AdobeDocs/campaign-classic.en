---
solution: Campaign Classic
product: campaign
title: Get started with surveys
description: Get started with Campaign surveys
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
---
# Get started with surveys{#about-surveys}

Adobe Campaign includes a graphical module to define and publish Web applications. This is used to create pages, such as an edit form on an extranet, or notification forms including data from the database with tables, charts, input forms, etc. This functionality lets you design and post web pages where users can look up or enter information.

The optional **Survey** module lets you create a new type of Web application to create and manage online questionnaires, such as forms to add or modify profile information, to subscribe to or unsubscribe from an information service, or a competition entry form. Once answers have been collected, they are stored in the database or in local variables. The data model can be extended dynamically via the answers given to questionnaires. You can view the results in real time, filter the responses, and analyze them using dedicated charts.

This chapter details the method for creating and managing **Surveys**, field and page management, storage modes and records.

The steps for creating a standard Web form are detailed in [this section](../../web/using/about-web-forms.md).

Web application management is detailed in [this section](../../web/using/about-web-applications.md). Please refer to this chapter for more information.

>[!CAUTION]
>
>For privacy reasons, we recommend to use HTTPS for all external resources.

## Feature scope {#campaign-surveys-scope}

In Adobe Campaign, Web applications in general let you access the following functionalities:

* Multiple-page form creation,
* Multilingual survey management with an integrated translation tool,
* Graphical page management interface, multiple-column page layout,
* Rendering personalization and field position,
* Conditional display of survey fields according to answers,
* Conditional page display,
* Checking information before approval, depending on the type of data expected (number, email address, dates, etc.) and mandatory fields,
* Email invitations/notifications,
* Personalization of error and end messages,
* Use of images, videos, hypertext links, captcha, etc.

>[!NOTE]
>
>All configurations linked to Web forms are detailed in [this section](../../web/using/about-web-forms.md). Refer to this document for details on concepts and on Web form functionalities using Adobe Campaign.

The optional survey creation module (**Survey**) offers the following additional functionalities:

* Dynamic extension of the database: creation of answers which aren't part of the initial data model. For more on this, refer to [Storing collected answers](../../web/using/managing-answers.md#storing-collected-answers).
* Score management. For more on this, refer to [Score management](../../web/using/managing-answers.md#score-management).
* Random displaying of questions. For more on this, refer to [Adding questions](../../web/using/building-a-survey.md#adding-questions).
* Real time tracking of answers. For more on this, refer to [Response tracking](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Generating dedicated reports. For more on this, refer to [Reports on surveys](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Compared to Web applications, surveys have a simplified graphical interface with a reduced number of editing controls.

## Surveys implementation steps {#surveys-implementation-steps}

Apply the following steps to create and deliver a survey and process its results:

1. Create the pages of the survey and their content (input fields, drop-down lists, questions, etc.). 
1. Define how answers should be saved.

   A data pre-loading step can be inserted in order to pre-load the form with data already in the database. You can also add a test box.

1. Publish, then deliver the survey to recipients (e.g. include link in a delivery or in a website).
1. Monitor responses and view reports.

For more information on configuring and sequencing these steps, refer to [this section](../../web/using/about-web-forms.md). Only configurations specific to surveys are detailed in this chapter.

## Surveys configuration {#surveys-configuration}

Surveys are stored in the **[!UICONTROL Resources > Online > Web Applications]** node of the Adobe Campaign tree. Configurations are found in the following folders:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contains the rendering templates for Web form presentation (applications and surveys). 
* **[!UICONTROL Resources > Templates > Web application templates]**: contains the form templates. To create a form, you need to start with a template.

>[!NOTE]
>
>Configuration information is available in [this section](../../web/using/about-web-forms.md).
