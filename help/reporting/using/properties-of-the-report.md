---
product: campaign
title: Properties of the report
description: Learn more about the report properties settings
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
TQID: https://experienceleague.adobe.com/NAcXKBNoDJRopQf-QpqnFhwxFRvvScp7xShJotE0s1A
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: cc72dcf1-72e1-48cc-b434-e7c27d62d67c
    internal-label: Accessibility
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic Reporting
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
    internal-label: Customize reports
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
    internal-label: Cubes and multidimensional analysis
---
# Properties of the report{#properties-of-the-report}

 

You can fully personalize and configure your report to suit your needs. To do this, edit its properties. Report properties are accessed via the **[!UICONTROL Properties]** button above the activity sequence chart.

![](assets/s_ncs_advuser_report_properties_01.png)

General properties are described below. Advanced capabilities configured in the **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** and **[!UICONTROL Scripts]** tabs are described [in this section](../../reporting/using/advanced-functionalities.md).

## General properties {#overall-properties}

In the **[!UICONTROL General]** tab of the report properties, you can edit the settings listed below:

* The label and the internal name of the report. The **[!UICONTROL Internal name]** is used in the report final URL. It should not be changed after the report creation.

* The report **Folder** is selected during report creation. A best practice is to create a dedicated folder for custom reports so that they are not mixed with [built-in reports](../../reporting/using/about-campaign-built-in-reports.md).

* The **Storage** is selected when creating the report. To change the data table of the report, click the **[!UICONTROL Select link]** icon to the right of the **[!UICONTROL Document type]** field.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* The **Access control** parameters. These settings are described below.

## Control access to the report {#report-accessibility}

A report can be accessed in the Adobe Campaign console or with a web browser. In this case, it can be necessary to configure the report access control as shown below.

![](assets/s_ncs_advuser_report_properties_02b.png)

Possible options are:

* **[!UICONTROL Anonymous access]**: this option enables unrestricted access to the report. However, no manipulation is possible.

  Permissions of the 'webapp' technical operator are used to display report elements. Learn more [in this section](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**: this option enables Adobe Campaign operators to access it once they are logged on.
* **[!UICONTROL Specific account]**: this option lets you execute the report with the rights of the operator selected in the **[!UICONTROL Operator]** field.

## Translate your report {#report-localization}

You can configure the languages which you want the report to be translated into. To do this, click the **[!UICONTROL Localization]** tab.

![](assets/s_ncs_advuser_report_properties_06.png)

The editing language is the language which you write in. When you add a language, the sub-tab appears in the report editing page.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>For more on web page localization in Campaign, refer to [this section](../../web/using/translating-a-web-form.md).

## Personalize HTML rendering {#personalizing-html-rendering}

In the **[!UICONTROL Rendering]** tab, you can personalize the data display mode for the page. You can select:

* The navigation type in the report: via buttons or links.
* The default position of labels for report elements. This position can be overloaded for each element.
* The template or theme used for generating report pages.

![](assets/s_ncs_advuser_report_properties_08.png)

## Personalizing the error page {#personalizing-the-error-page}

The **[!UICONTROL Error page]** tab lets you configure the message that will come up in case of an error in the report display.

You can define texts and link them to specific identifiers to manage report localization. For more on this, refer to [Adding a header and a footer](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
