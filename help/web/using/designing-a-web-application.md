---
product: campaign
title: Design a web application
description: Design a web application
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
TQID: https://experienceleague.adobe.com/8HdoOgOBgZgI3-Kxnn-I0kW5zyTSBfUtM0IoLGBvHag
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
    internal-label: Web Apps
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
    internal-label: Web Forms
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
    internal-label: Landing pages
---
# Design a web application{#designing-a-web-application}

 

Web applications are created and managed according to the same principle as [web forms](about-web-forms.md).

>[!CAUTION]
>
>Use the **[!UICONTROL Preview]** sub-tab to check errors during web application design. Note that the profile test used to preview your web application needs to be in a folder with **[!UICONTROL Access rights]** for the **[!UICONTROL Web application agent]** operator. </br>Until the Web application is published, changes are not exposed to end users.

## Inserting charts in a Web application {#inserting-charts-in-a-web-application}

You can include charts in Web applications. To do this, use the drop-down list of charts in the task bar to select the type of chart to be inserted.

![](assets/s_ncs_admin_webapps_bar_graph.png)

You can also select the **[!UICONTROL Add a chart]** menu.

![](assets/s_ncs_admin_webapps_graph.png)

## Inserting tables in a Web application {#inserting-tables-in-a-web-application}

To add a table, use the drop-down list of tables in the task bar to select the type of table to be used.

![](assets/s_ncs_admin_webapps_bar_table.png)

You can also select the type of table in the drop-down menu.

![](assets/s_ncs_admin_webapps_table.png)

## Overview-type Web applications {#overview-type-web-applications}

The Adobe Campaign interface uses many Web applications to access, manage, and interact with recipients, deliveries, campaigns, stocks, etc.

They are seen in the interface in the form of dashboards with only one page.

The out-of-the-box Web applications are stored in the **[!UICONTROL Administration > Configuration > Web applications]** node.

## Edit forms-type Web applications {#edit-forms-type-web-applications}

Edit form Web applications for an extranet are characterized by:

* A preloading box

  In most cases, the data to be displayed must be preloaded. Because the users who access these forms are identified (via an access control), preloading is not necessarily encrypted.

* A save box
* Adding pages

  Whereas "Overview"-type Web applications all have a single page, edit forms can offer a sequence of pages based on specific criteria (tests, selections, profile of connected operator, etc.).

