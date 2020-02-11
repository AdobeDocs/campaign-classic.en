---
title: Properties of the report
seo-title: Properties of the report
description: Properties of the report
seo-description: 
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
index: y
internal: n
snippet: y
---

# Properties of the report{#properties-of-the-report}

## Overview {#overview}

You can fully personalize and configure your report to suit your needs. To do this, edit its properties. Report properties are accessed via the Property button found above the activity sequence chart.

![](assets/s_ncs_advuser_report_properties_01.png)

## Overall properties {#overall-properties}

The **[!UICONTROL General]** tab lets you view or alter the label and the schema which the report concerns. These elements are entered during report creation.

We do not recommend changing the **[!UICONTROL Internal name]** : this is used in the report access URL.

The report template is selected during report creation and cannot be altered later on.

To change the table which the report concerns, click the **[!UICONTROL Select link]** icon to the right of the **[!UICONTROL Document type]** field. To view the available fields in the selected table, click the **[!UICONTROL Magnifier]** icon.

![](assets/s_ncs_advuser_report_properties_02.png)

## Report accessibility {#report-accessibility}

A report can be accessed beyond the Adobe Campaign console, for instance via a Web browser. In this case, it can be necessary to configure the report access control as shown below.

![](assets/s_ncs_advuser_report_properties_02b.png)

The overall principle is as follows:

* The **[!UICONTROL Anonymous access]** option enables unrestricted access to the report. However, no manipulation is possible.

  The rights of the default ('webapp') report operator are used to display report elements.

* The **[!UICONTROL Access control]** option enables Adobe Campaign operators to access it once they are logged on.
* The **[!UICONTROL Specific account]** option lets you execute the report with the rights of the operator selected in the **[!UICONTROL Operator]** field.

Web form properties are detailed in [this page](../../web/using/about-web-forms.md).

## Managing report localization {#managing-report-localization}

You can configure the languages which you want the report to be translated into. To do this, click the **[!UICONTROL Localization]** tab.

![](assets/s_ncs_advuser_report_properties_06.png)

The editing language is the language which you write in. When you add a language, the sub-tab appears in the report editing page.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>For more on this, refer to the appropriate section of [this section](../../web/using/translating-a-web-form.md).

## Personalizing HTML rendering {#personalizing-html-rendering}

In the **[!UICONTROL Rendering]** tab, you can personalize the data display mode for the page. You can select:

* The chart rendering engine: Adobe Campaign offers two different modes for generating chart rendering. By default, the rendering engine is HTML 5. If necessary, you can select Flash rendering. 
* The navigation type in the report: via buttons or links.
* The default position of labels for report elements. This position can be overloaded for each element.
* The template or theme used for generating report pages.

Web form properties are detailed in [this page](../../web/using/about-web-forms.md).

![](assets/s_ncs_advuser_report_properties_08.png)

## Defining additional settings {#defining-additional-settings}

The **[!UICONTROL Parameters]** tab lets you create additional settings for the report: these settings will be passed into the URL during the call up.

Web form properties are detailed in [this page](../../web/using/about-web-forms.md).

>[!CAUTION]
>
>For security reasons, these parameters must be used with great caution.

To create a new setting:

1. Click the **[!UICONTROL Add]** button and enter the name of the setting.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. If necessary, specify whether or not the setting will be mandatory.
1. Select the type of setting you want to create: **[!UICONTROL Filter]** or **[!UICONTROL Variable]**.

   The **[!UICONTROL Filter entities]** option lets you use a field of the database as a parameter.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   The data is recovered directly at the entity level: **ctx/recipient/@account**.

   The **[!UICONTROL Variable]** option lets you create or select a variable which will be passed as a parameter of the URL and can be used in the filters.

The **[!UICONTROL Response HTTP headers]** allows you to prevent clickjacking when using iframe. To avoid this, you can choose the **[!UICONTROL X-Frame-options header]** behaviour:

* **[!UICONTROL None]**: The report will have no **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Allow from URL]**: Allows you to autorize specific URL or URL type.
* **[!UICONTROL Same as origin]**: Set by default for new reports and republished reports. The hostname will be the same as the report's URL.
* **[!UICONTROL Deny]**: H

## Adding variables {#adding-variables}

The **[!UICONTROL Variables]** tab contains the list of variables configured in the report. These variables are exposed in the context of the report and can be used in calculations.

Click the **[!UICONTROL Add]** button to create a new variable.

To view the definition of a variable, select it and click the **[!UICONTROL Detail...]** button.

![](assets/s_ncs_advuser_report_properties_10.png)

## Referencing scripts {#referencing-scripts}

The **[!UICONTROL Scripts]** tab lets you reference JavaScript codes that will be executed on the client and/or server side when the report page is called up.

For normal execution on the client side, the referenced scripts must be written in JavaScript and need to be compatible with most browsers. For more on this, refer to [this section](../../web/using/web-forms-answers.md).

## Personalizing the error page {#personalizing-the-error-page}

The **[!UICONTROL Error page]** tab lets you configure the message that will come up in case of an error in the report display.

You can define texts and link them to specific identifiers to manage report localization. For more on this, refer to [Adding a header and a footer](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)

