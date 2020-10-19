---
title: Advanced functionalities
seo-title: Advanced functionalities
description: Advanced functionalities
seo-description: 
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
---

# Advanced functionalities{#advanced-functionalities}

## Adding a script {#adding-a-script}

### Script activity {#script-activity}

This activity enables you to process data and easily create complex queries that don't enable SQL language.

Simply enter your query in the script window.

The **[!UICONTROL Texts]** tab enables you to define text strings. They may then be used with the following syntax: **$(Identifier)**. For more on using texts, refer to [Adding a header and a footer](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>We do NOT recommend using JavaScript code to create aggregates.

To create a history of your report, add the following line to your JavaScript query in order to save your archived data:

```
if( ctx.@_historyId.toString().length == 0 )
```

Otherwise current data will be displayed.

### External script {#external-script}

It's possible to use an external script that will be executed on the server and/or client side. To do this:

1. Edit the report properties and click the **[!UICONTROL Scripts]**.
1. Click **[!UICONTROL Add]** and select the script to be referenced.
1. Then select the execution mode.

   If you add several scripts, use the arrows of the toolbar to define their execution sequence.

   ![](assets/reporting_custom_js.png)

## Calling up another report {#calling-up-another-report}

### Jump activity {#jump-activity}

A jump is like a transition without an arrow: it lets you go from one activity to another or access another report.
