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

## ![](assets/do-not-localize/limited_2.png) Release 7.3.1 - Build 9352 {#release-7-3-1}

_July 1, 2022_

**What's new?**

<table> 
<thead>
<tr> 
<th> <strong>Time Sensitive notifications</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>With iOS 15, Apple added a notion of sensitive notification that gives control to the app developer to bypass Focus mode when a notification is considered as sensitive and then needs to reach the user in real-time.</p>
<p>Learn how to create a sensitive notification in the <a href="../../delivery/using/create-notifications-ios.md">detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Compatibility updates**

* Adobe Campaign SDK now supports Android 12 and iOS 15 for Push Notifications.
* Adobe Campaign is now compatible with MySQL 8.
* Adobe Campaign is now compatible with Windows 11.
* Adobe Campaign is now compatible with Debian 11.

Refer to the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Improvements**

* Following the end of life of Internet Explorer 11, the HTML rendering engine for Adobe Services in the console is now using Edge Chromium. Additionally, installation of Microsoft Edge Webview 2 runtime is now required for any client console installation (From Campaign Classic 7.3 build version). [Read more](../../installation/using/installing-the-client-console.md)
* The database connection management in Adobe Campaign has been improved to optimize stability.
* Microsoft Exchange Online OAuth 2.0 authentication for POP3 is now supported in Campaign. [Read more](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Fixed various issues when using an enrichment workflow activity with external data. (NEO-38069)
* The SAP Hana FDA connector has been updated to function with the latest SAP Hana database version (2.x).
* The Teradata FDA connector has been updated to function with the latest Teradata version (17).
* In 20.2, the support of token-based authentication for iOS deliveries was introduced for new deliveries and delivery templates. In 7.2, a patch was added to the postugrade to apply the token-based authentication support to a maximum of 10,000 previously created deliveries and delivery templates. In 7.3, the patch has been improved and the limit has been removed.

**Patches**

* Fixed an error from the previous build which prevented users from resizing the IMS login page.
* Fixed an error which occurred when installing the content manager package on an existing instance.
* Fixed an issue in the **Campaigns** menu where an "operation in progress" message was displayed continuously. 
* With Adobe Analytics enabled, fixed an issue that removed BID (Broadlog ID) and CID (Campaign ID) from the URL when sending an email with a URL without saving the delivery.
* Fixed an issue when uploading an image in the Public resources folder in an instance with Message Center specific configuration. The following error message would appear: "Unable to upload the images to the tracking servers".
* Fixed an issue that caused the system to crash when regenerating configuration in case of bad configuration files.
* Fixed an issue which could lead to delivery indicators not being updated correctly. (NEO-44827)
* Fixed an issue which could lead to a postupgrade error when using complex queries. (NEO-43648)
* Fixed an issue that could prevent webApps preview from working. (NEO-43242)
* Fixed an issue that could lead delivery preparation to fail when using an external target mapping file in a workflow with a Data loading (file) activity. (NEO-43691)
* Fixed an issue that could lead to crashes and required a complete restart of the instance. (NEO-44645)
* Fixed an issue which could prevent Workflow Heatmap from loading any result. (NEO-43360)
* Fixed an issue that could lead to connection issues when using the FDA external connector. (NEO-42722)
* Fixed an issue with proofs when using address substitution and control group exclusion. (NEO-39695)
* Fixed an issue which could lead to workflow failures due to a Snowflake connector issue. (NEO-46299)
* Fixed an issue which could freeze the client console due to an invalid character in a personnalization block. (NEO-45761)
* Fixed an issue that could lead to connection issues when creating an external account for Snowflake as an external database. (NEO-45744)
* Fixed an issue that could lead to display table information protected by a visibleIf attribute. (NEO-37865)
* Fixed an issue that could display the "$ is not defined" error message during the delivery analysis phase. (NEO-32940)
* Fixed an issue that caused deliveries to be associated with a wrong eventType. (NEO-45743)
* Fixed an issue that could lead to crashes due to intermittent core dumps (NEO-30549)
* Fixed an issue that could lead to crashes when using erroneous HTML code in a delivery. (NEO-40385)
* Fixed an issue that could prevent non admin users from accessing the **Analysis** tab in delivery properties. (NEO-34025)

## ![](assets/do-not-localize/green_2.png) Release 7.2.2 - Build 9349 {#release-7-2-2}

_March 1, 2022_

>[!NOTE]
>
> This build is compatible with v7.2.1 Client Console.

**Patches**

* Fixed an issue, when configuring the **Web Analytics** external account, which caused the integration status to always show "Integration successful" even when errors occurred. (NEO-36672)
* Fixed several postupgrade errors related to the sequence ID mechanism when having negative IDs. (NEO-43205, NEO-42846, NEO-42845)
* Fixed an issue when using the **Web Analytics** external account with recurring and continuous deliveries, which caused data from the external account to be partially lost. (NEO-38548)
* Fixed an issue which slowed down postupgrade when updating the NmsActiveContact table. (NEO-43206)
* Fixed a postupgrade failure issue which occurred if out-of-the-box folders had been moved from the **Administration** node to any other location. (NEO-42875)
* Fixed an issue when using an **Update data** workflow activity which could prevent the recipient schema from being updated with recipient data from a Google Cloud external database. (NEO-42343)
* Fixed an issue during postupgrade related to the Adobe Analytics connector. (NEO-43318, NEO-38136)
* Fixed an overwritten CUID by 'VALUE_TO_CHANGE' issue during postupgrade. (NEO-43267)
* Fixed an issue which led to errors when synchronizing the mid-sourcing and marketing instances on a multi-mid configuration. (NEO-10432)
* Fixed an issue which led to an error when refreshing the deliverability workflow when having more than 1000 broadlogs at the same time. (NEO-40276)
* Fixed an issue which prevented the open ratio and click ratio delivery indicators from being updated automatically. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Release 7.2.1 - Build 9346 {#release-7-2-1}

_January 10, 2022_

**Security enhancement**

Several security improvements have been made to FDA accounts:

* When configuring your FDA external account, you can now login to your Snowflake account using Key pair authentication for enhanced authentication security. [Read more](../../installation/using/configure-fda-snowflake.md)
* When configuring your FDA external account, you can now login to your Azure Synapse Analytics account using the System-assigned managed identity. [Read more](../../installation/using/configure-fda-synapse.md#azure-external)
* All references to the log4j library have been removed from Campaign to ensure optimal security.

**Compatibility updates**

Adobe Campaign is now compatible with Windows Server 2019. Refer to the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md#OperatingSystems).

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
* Improved performance for transactional messaging processing time. (NEO-40370)

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
