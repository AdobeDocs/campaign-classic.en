---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Data Connector
description: Adobe Analytics Data Connector
feature: Overview
role: Business Practitioner, Administrator
level: Beginner
exl-id: 5bd12f65-f468-41ab-bbae-e59a6592a803
---
# Adobe Analytics Data Connector{#adobe-analytics-data-connector}

## About Data Connector integration {#about-data-connector-integration}

>[!IMPORTANT]
>
>Adobe Analytics Data Connector is not compatible with Transactional messaging (Message Center).

Data Connector (previously known as Adobe Genesis) allows Adobe Campaign and Adobe Analytics interact through the **Web Analytics connectors** package. It forwards data to Adobe Campaign in the form of segments concerning user behavior following an email campaign. Conversely, it sends indicators and attributes of email campaigns delivered by Adobe Campaign to Adobe Analytics - Data connector.

Using Data connector, Adobe Campaign has a way of measuring internet audience (Web Analytics). Thanks to these integrations, Adobe Campaign can recover data on visitor behavior for one or more sites following a marketing campaign, and (after analysis) run re-marketing campaigns with a view to converting them into buyers. Conversely, the Web analytics tools enable Adobe Campaign to forward indicators and campaign attributes to their platforms.

For more information on the implementation of the integration Adobe Analytics with Adobe Campaign, refer to this [documentation](https://helpx.adobe.com/marketing-cloud/how-to/analytics-ac.html).

The action fields for each tool are as follows:

* Web analytics' role:

    1. marks the email campaigns launched with Adobe Campaign,
    1. saves recipient behavior, on the site they browsed after clicking the campaign email, in the form of segments. Segments concern abandoned products (viewed but not added to the cart or purchased), purchases or cart abandonments.

* Adobe Campaign's role:

    1. sends the indicators and campaign attributes to the connector, which in turn forwards them to the Web analytics tool,
    1. recovers and analyzes segments,
    1. triggers a re-marketing campaign.

## Setting up the integration {#setting-up-the-integration}

To set up the Data connector, you must connect to your Adobe Campaign instance and perform the following operations:

In Adobe Analytics:

1. Create a new **[!UICONTROL Report suite]**. 

   For the detailed procedure on Report suite creation, refer to this [section](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en#prerequisites).

1. From your **[!UICONTROL Report suite]**, create two **[!UICONTROL Conversion variables]**: one for the Delivery name and one for the BroadlogID. 

   To learn how to edit **[!UICONTROL Conversion variables]**, refer to this [section](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/t-conversion-variables-admin.html?lang=en#admin-tools).

1. Then, configure ten **[!UICONTROL Success events]**. 

   To learn how to configure **[!UICONTROL Success events]**, refer to this [section](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/success-events/t-success-events.html?lang=en#admin-tools)

When your report suite is configured, you will need to configure the **[!UICONTROL External accounts]** in Adobe Campaign Classic:

1. Install the **[!UICONTROL Web Analytics connectors]** package in Adobe Campaign.

1. Go to the **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** folder of the Adobe Campaign tree.

1. Click **[!UICONTROL New]** above the list of external accounts.

1. Use the drop-down list to select the **[!UICONTROL Web Analytics]** type.

1. Select **[!UICONTROL Adobe Analytics]** from the **[!UICONTROL Integration]** drop-down.

1. Click **[!UICONTROL Configure]** next to the **[!UICONTROL Integration]** drop-down.

1. From the **[!UICONTROL Configure Analytics integration]** window, map your external account with your previously created Report suite providing the following information:

   * **[!UICONTROL E-Mail]**
   * **[!UICONTROL IMS Org]**
   * **[!UICONTROL Analytics Company]**
   * **[!UICONTROL Report Suite]**

1. From the **[!UICONTROL eVars]** category, map the two **[!UICONTROL Conversion variables]** configured in [!DNL Adobe Analytics].

1. From the **[!UICONTROL Events]** category, map the ten **[!UICONTROL Success events]** configured in [!DNL Adobe Analytics].

1. Click **[!UICONTROL Submit]** when done. 

1. Settings can be viewed clicking **[!UICONTROL Data Settings]** from your **[!UICONTROL External account]**.

1. If needed, you can add or remove segments from the **[!UICONTROL Update Segments]** Tab.

After save occurs, the Campaign creates the following components on analytics end.
9 OOTB Classifications
A Data Source
A Calculated Metric
Segment 'Genesis Remarketing - Product Views'
Segment 'Genesis Remarketing - Product Purchases'
Segment 'Genesis Remarketing - Cart Abandonment'
The modal displays the status of the creation/updation of components. 
Messages displayed when creation of components is in-progress
