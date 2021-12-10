---
product: campaign
title: Latest Release
description: Learn more about Campaign Classic latest release
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
---
# Latest release{#latest-release}

![](../../assets/v7-only.svg)

This page lists new capabilities, improvements and fixes coming with the **latest Campaign Classic Release**.

Understand Campaign build statuses in [this page](rn-overview.md). 

## ![](assets/do-not-localize/blue_2.png) Release 7.2.1 - Build XXXX {#release-7-2-1-build-xxxx}

**Security enhancement**

Several security improvements have been made to the FDA accounts:

* ODBC drivers are now directly installed with Adobe Campaign Third Parties. Manual steps are no longer required to install the drivers.
* Google Big Query is now available for Hosted deployments.

[Read more](../../installation/using/configure-fda.md)

**Improvements**

* Critical fixes have been applied regarding the Microsoft Dynamics Connector web API:
    * Fixed an issue which could cause data import from Microsoft CRM to fail or not work if the filter condition contained lookup fields.
    * Fixed an issue, during an import triggered by a workflow, which caused the null values of string-type fields to be saved as Null instead of empty values.
    * Fixed an issue which led to the following error for data import or export using web API calls: "Invalid URI: The URI scheme is too long".
    * Fixed an issue, during an import from Microsoft Dynamics 365, which prevented the lookup fields data from being imported.

**Other changes**

* Following their deprecation, Microsoft CRM, Salesforce, Oracle CRM On Demand action activities have been removed from the interface.
* The **[!UICONTROL Encrypted identifier]** field has been added to the visitor schema (nms:visitor). This field is calculated and is to be used for web applications.
* CRM datasources can now be used with the **Change data source** activity.
* A new option has been added in the **Error management** properties of workflow activities: The **Abort on error** option will stop automatically the workflow. You will not be able to restart it afterwards. (NEO-29661)
* A dedicated sequence is now used to generate the primary keys for the nmsGroup table, which is used to create statistical groups of recipients. Previously, the xtknewId sequence was used. (NEO-30832)

**Patches**

* Fixed an issue when creating a delivery which led to an error in the **Images** tab of the **Tracking & images** window. This occurred when using an auto proxy configuration. (NEO-33260) 
* Fixed an issue which could prevent you from uploading a file on a Debian 10 server (HTTPS) in synchronous mode.
* Fixed an issue which could prevent records of the deliveries statistics table (`nmsDeliveryLogStats`) from being purged from the mid-sourcing instance during database cleanup after the related deliveries had been deleted. (NEO-31034)
* Fixed an issue which prevented you from sending mobile app notifications in iOS while using token-based authentication (NEO-38640).
* Added support for batch update operations using the CRM connector activity.
* Fixed an issue which could display script error messages when trying to create and configure reports (NEO-38393). 
* Fixed an issue which could cause the tracking workflow to fail in Oracle due to high volume of delivery indicators being updated simultaneously (NEO-39653).
* Fixed an issue which could prevent a delivery from being sent due to an error occurring while executing a control typology (NEO-39833).
* Fixed an issue in landing pages which could prevent special characters from displaying correctly in the HTML pages of online survey responses (NEO-39438).
* Fixed an issue which could prevent Campaign Classic console from working when right-clicking on any of the folders from the Explorer tab (NEO-38884).
* Fixed an error when using a previously created delivery template linked to a Web Analytics account in a new delivery where the Web Analytics configuration was missing. (NEO-28666)
* Fixed an issue that could prevent you from previewing mobile deliveries that were attached to a workflow.
* Fixed an error that prevented personalized tracking URLs from being redirected when the URL signature mechanism for tracking links was enabled.
* Fixed an issue that could cause postupgrade failures due to an index management issue.
* Fixed an error which occurred when using Lookup field data types with Microsoft Dynamics CRM in **Import** or **Export** workflow activities.
* Fixed an issue which could prevent users from login to the console due to a proxy configuration issue. (NEO-38388)
* Fixed a regression issue which prevented the **Purge folder** functionality from working correctly. (NEO-37459)
* Fixed an issue which led to a bad request error when using xml-data fields with the Microsoft Dynamics CRM account if the referenced xml contained double quotes.
* Fixed an issue that caused network timeout issues to be incorrectly logged as script interruption issues instead of network errors. This issue occurred in the case of HTTP requests that were included in JavaScript activities. (NEO-38079)
* Fixed an issue that returned incorrect results when running the Amazon Redshift HoursDiff and MinutesDiff functions while trying to extract the time component.(NEO-31673)
* Fixed an issue which prevented the **Hot Clicks** report from loading for deliveries since build 9182. (NEO-28900)
* Fixed an error which replaced the & symbol in an URL with the character entity reference (`&amp;`) preventing users to access the URL linked to a QR code. (NEO-28621)
* Fixed an issue which created a new external account everytime a user created a new campaign workflow and a delivery activity linked to a Web Analytics account. This was caused by a missing id in the webAnalyticsAccount delivery object. (NEO-39691)
* Fixed an issue which could prevent the **Read list** workflow activity from working when the list was identified in the database with a negative ID. (NEO-39607)
* Fixed an issue with could lead the **Mid-sourcing (delivery logs)** workflow to fail. (NEO-39662)
* Fixed an issue that could prevent you from previewing email deliveries that were attached to a workflow. (NEO-37840)
* Fixed an issue that could cause valid tables that contained list values to be deleted by the database cleanup workflow. (NEO-34911)
* Fixed an issue that could cause the billing workflow to crash on marketing instances.
