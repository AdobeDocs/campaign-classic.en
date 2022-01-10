---
product: campaign
title: Latest Release
description: Latest Campaign Classic v7 Release Notes
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
---
# Latest release{#latest-release}

![](../../assets/v7-only.svg)

This page lists new capabilities, improvements and fixes coming with the **latest Campaign Classic v7 Release**. Every new build comes with a status which is materialized by a color. Learn more about Campaign Classic v7 build statuses in [this page](rn-overview.md). 

## ![](assets/do-not-localize/green_2.png) Release 7.2.1 - Build 9346 {#release-7-2-1}

_January 10, 2022_

**Security enhancement**

Several security improvements have been made to FDA accounts:

* ODBC drivers are now directly installed with Adobe Campaign Third Parties. Manual steps are no longer required to install these drivers.
* When configuring your FDA external account, you can now login to your Snowflake account using Key pair authentication for enhanced authentication security. [Read more](../../installation/using/configure-fda-snowflake.md)
* When configuring your FDA external account, you can now login to your Azure Synapse Analytics account using the System-assigned managed identity. [Read more](../../installation/using/configure-fda-synapse.md#azure-external)


**Improvements**

* Microsoft Dynamics CRM 365 Connector

    Critical fixes have been applied regarding the Microsoft Dynamics Connector web API:

    * Fixed an issue, during an import triggered by a workflow, which caused the null values of string-type fields to be saved as Null instead of empty values.
    * Fixed an issue which led to the following error for data import or export using web API calls: "Invalid URI: The URI scheme is too long".
    * Fixed various issues when importing, from Microsoft Dynamics 365, data containing lookup fields.

* Google BigQuery FDA Connector

    * Google BigQuery FDA Connector is now available for Hosted deployments. [Read more](../../installation/using/configure-fda-google-big-query.md)
    * Added support to enable connections to a proxy server for Google BigQuery FDA connector. Required proxy options can be set through the Options field in the external account configuration. [Read more](../../installation/using/configure-fda-google-big-query.md#google-external)

**Other changes**

* Following their deprecation, Microsoft CRM, Salesforce, Oracle CRM On Demand action activities have been removed from the interface. To configure the data synchronization between Adobe Campaign and a CRM system, you can use the CRM connector activity. [Read more](../../workflow/using/crm-connector.md)
* The **[!UICONTROL Encrypted identifier]** field has been added to the visitor schema (nms:visitor). This field is calculated and is to be used for web applications. This applies when the Line channel is configured on the mid-sourcing instance.
* CRM datasources can now be used with the **Change data source** activity.
* A new option has been added in the **Error management** properties of workflow activities: The **Abort on error** option will stop automatically the workflow. You will not be able to restart it afterwards (NEO-29661). [Read more](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* A dedicated sequence is now used to generate the primary keys for the nmsGroup table, which is used to create statistical groups of recipients. Previously, the xtknewId sequence was used. (NEO-30832)
* Added support for batch update operations using the CRM connector activity.

**Patches**

* Fixed an issue when creating a delivery which led to an error in the **Images** tab of the **Tracking & images** window. This occurred when using an auto proxy configuration. (NEO-33260) 
* Fixed an issue which could prevent you from uploading a file on a Debian 10 server (HTTPS) in synchronous mode.
* Fixed an issue which could prevent records of the deliveries statistics table (`nmsDeliveryLogStats`) from being purged from the mid-sourcing instance during database cleanup after the related deliveries had been deleted. (NEO-31034)
* Fixed an issue which prevented you from sending mobile app notifications on iOS while using token-based authentication (NEO-38640).
* Fixed an issue which could display script error messages when trying to create and configure reports (NEO-38393). 
* Fixed an issue which could cause the tracking workflow to fail on Oracle due to high volumes of delivery indicators being updated simultaneously (NEO-39653).
* Fixed an issue which could prevent a delivery from being sent due to an error occurring while executing a control typology (NEO-39833).
* Fixed an issue in landing pages which could prevent special characters from displaying correctly in the HTML pages of online survey responses (NEO-39438).
* Fixed an issue which could prevent the Campaign Classic console from working when right-clicking on any of the folders from the Explorer tab (NEO-38884).
* Fixed an error when using a previously created delivery template linked to a Web Analytics account in a new delivery where the Web Analytics configuration was missing. (NEO-28666)
* Fixed an issue that could prevent you from previewing mobile deliveries that were attached to a workflow.
* Fixed an error that prevented personalized tracking URLs from being redirected when the URL signature mechanism for tracking links was enabled.
* Fixed an issue that could cause postupgrade failures due to an index management issue.
* Fixed an error which occurred when using lookup field data types with Microsoft Dynamics CRM in **Import** or **Export** workflow activities.
* Fixed an issue which could prevent you from login to the console due to a proxy configuration issue. (NEO-38388)
* Fixed a regression issue which prevented the **Purge folder** functionality from working correctly. (NEO-37459)
* Fixed an issue which led to a bad request error when using xml-data fields with the Microsoft Dynamics CRM account if the referenced xml contained double quotes.
* Fixed an issue that caused network timeout issues to be incorrectly logged as script interruption issues instead of network errors. This issue occurred in the case of HTTP requests that were included in JavaScript activities. (NEO-38079)
* Fixed an issue that returned incorrect results when running the Amazon Redshift HoursDiff and MinutesDiff functions while trying to extract the time component.(NEO-31673)
* Fixed an issue which prevented the **Hot Clicks** report from loading for deliveries since build 9182. (NEO-28900)
* Fixed an error which replaced the & symbol in an URL with the character entity reference (`&amp;`) preventing users to access the URL linked to a QR code. (NEO-28621)
* Fixed an issue which created a new external account everytime a user created a new campaign workflow and a delivery activity linked to a Web Analytics account. This was caused by a missing ID in the webAnalyticsAccount delivery object. (NEO-39691)
* Fixed an issue which could prevent the **Read list** workflow activity from working when the list was identified in the database with a negative ID. (NEO-39607)
* Fixed an issue with could lead the **Mid-sourcing (delivery logs)** workflow to fail. (NEO-39662)
* Fixed an issue that could prevent you from previewing email deliveries that were attached to a workflow. (NEO-37840)
* Fixed an issue that could cause valid tables that contained list values to be deleted by the database cleanup workflow. (NEO-34911)
* Fixed an issue that could cause the billing workflow to crash on marketing instances.
