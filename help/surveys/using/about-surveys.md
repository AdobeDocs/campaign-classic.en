---
product: campaign
title: Get started with surveys
description: Get started with Campaign surveys
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
---
# Get started with surveys{#about-surveys}

Adobe Campaign includes a graphical module to define and publish Web applications. This is used to create pages, such as an edit form on an extranet, or notification forms including data from the database with tables, charts, input forms, etc. Use this capability to design and post web pages in which users can look up or enter information.

The optional **Survey** add-on lets you create a new type of Web application to create and manage online questionnaires, such as forms to add or modify profile information, to subscribe to or unsubscribe from an information service, or a competition entry form. Once answers have been collected, they are stored in the database or in local variables. The data model can be extended dynamically via the answers given to questionnaires. You can view the results in real time, filter the responses, and analyze them using dedicated charts.

This chapter details how to create and manage **Surveys**, field and page management, storage modes and records.

[!DNL :bulb:] Learn how to create your first survey in [this page](getting-started-with-surveys.md).

>[!NOTE]
>
>* Detailed steps for creating a standard Web form are available in [this document](../../web/using/about-web-forms.md).
>
>* Web application management is detailed in [this document](../../web/using/about-web-applications.md). Please refer to this chapter for more information.

## Feature scope {#campaign-surveys-scope}

In Adobe Campaign, use [Web applications](../../web/using/about-web-forms.md) to:

* Create multiple-page forms,
* Manage multilingual forms with an integrated translation tool,
* Manage graphical interface, multiple-column page layout,
* Add personalization and define field position,
* Condition display of survey fields according to answers,
* Condition page display,
* Check information before approval, depending on the type of data expected (number, email address, dates, etc.) and mandatory fields,
* Send email invitations/notifications,
* Personalize error and end pages,
* Add images, videos, hypertext links, captcha, etc., in forms

The optional survey creation module offers a user-friendly UI and the following additional functionalities:

* Dynamic extension of the database: creation of answers which aren't part of the initial data model. [Learn more](../../surveys/using/managing-answers.md#storing-collected-answers).
* Score management. [Learn more](../../surveys/using/managing-answers.md#score-management).
* Random displaying of questions. [Learn more](../../surveys/using/building-a-survey.md#adding-questions).
* Real time tracking of answers. [Learn more](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Generating dedicated reports. [Learn more](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Implementation steps {#surveys-implementation-steps}

Apply the following steps to create and deliver a survey and process its results:

1. Create the pages of the survey and their content (input fields, drop-down lists, questions, etc.). 
1. Define how answers should be saved. A data pre-loading step can be inserted in order to pre-load the form with data already in the database. You can also add a test box.
1. Publish, then deliver the survey to recipients (e.g. include link in a delivery or in a website).
1. Monitor responses and view reports.

For more information on configuring and sequencing these steps, refer to [this document](../../web/using/about-web-forms.md). Only configurations specific to surveys are detailed in this chapter.

>[!CAUTION]
>
>For privacy reasons, we recommend to use HTTPS for all external resources.

## Settings {#settings}

By default, surveys are available in the **[!UICONTROL Resources > Online > Web Applications]** node of the Adobe Campaign tree. 

Settings are stored in the following folders:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contains the rendering templates for Web form presentation (applications and surveys). 
* **[!UICONTROL Resources > Templates > Web application templates]**: contains the form templates. To create a form, you need to start with a template.

>[!NOTE]
>
>Settings details are available in [this document](../../web/using/about-web-forms.md).
