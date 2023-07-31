---
product: campaign
title: Latest Release
description: Latest Campaign Classic v7 Release Notes
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
---
# Latest release{#latest-release}

This page lists new capabilities, improvements and fixes coming with the **latest Campaign Classic v7 Release**. Every new build comes with a status which is materialized by a color. Learn more about Campaign Classic v7 build statuses in [this page](rn-overview.md). 

## Release 7.3.3 - Build 9359 {#release-7-3-3}

[!BADGE General Availability]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="General Availability"}

>[!CAUTION]
>
>Client Console upgrade is mandatory. Learn how to upgrade your Client Console in this [page](../../installation/using/installing-the-client-console.md).

_March 20, 2023_

**Security enhancement**

* To optimize security, Tomcat has been updated from version 8.5.81 to 8.5.85. (NEO-56936)

**Improvements**

* The Billing workflow has been improved to optimize performance. (NEO-47658)
* The tracking workflow has been improved to optimize performance in case of high delivery size. (NEO-45064)
* Tracking management has been improved to fix possible issues with dynamic parameters in URLs. Tracking management v3 now handles ajax type URLs (with parameters after a '#') and prevents third-party tools from modifying tracking URLs. To apply this change, you need to contact Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Patches**

* Fixed an issue which could prevent iOS proof push notifications from being sent from the control instance (Transactional Messaging context). (NEO-54713)
* Fixed an issue which could prevent you from scrolling in the **Edit** tab of the Digital Content Editor (DCE). (NEO-54474)
* Fixed an issue, when two enrichment activities were using the same name identifier in their linking, which led the second enrichment activity to use the links of the first one. (NEO-48851)

## Release 7.3.2 - Build 9356 {#release-7-3-2}

[!BADGE Limited Availability]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Limited Availability"}

_November 21, 2022_

>[!CAUTION]
>
>Client Console upgrade is mandatory. Learn how to upgrade your Client Console in this [page](../../installation/using/installing-the-client-console.md).

**Compatibility updates**

* Adobe Campaign is now compatible with PostgreSQL 14. For more information, refer to this [technote](../../technotes/using/tech-stack-upgrade.md).

* Following the end of life of Microsoft Internet Explorer 11, the HTML rendering engine for dashboards in the client console is now using Edge Chromium. (NEO-20741)

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Improvements**

* The Google BigQuery connector now fully supports boolean fields. (NEO-49181)
* You can now configure the IMS cookies validity duration in the `Configuration for the redirection service` section of the serverConf.xml file. This applies to the following cookies: `uuid230`, `nllastdelid` and `AMCV_` (NEO-42541)
* The IP can now be hidden in the "/r/test" request by setting `showSourceIP` to false in the redirection node of the serverConf.xml file. [Read more](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Deprecated features**

* Social Marketing with Facebook is now deprecated. You can use Twitter integration to post on social media, or work with Adobe to create a custom channel.
* ACS Connector (Prime offering) is now deprecated. You can use Campaign export/import capabilities to extract and inject data in both products.

Learn more in the [Deprecated and removed features page](deprecated-features.md).

**Other changes**

* Web logs have been improved: `logonEscalation` warnings are now only displayed for users with admin privileges. (NEO-47167)
* To avoid errors, the **Collect data for Heatmap service** (collectDataHeatMapService) workflow is now stopped by default. (NEO-33959)
* Various improvements were implemented to optimize CPU usage for the campaigns dashboard. (NEO-46417)
* To prevent crashes, the loadLibraryDebug JS method has been removed. (NEO-46968)
* The remaining references to the log4j library have been removed from the Campaign installation on Windows. (NEO-44851)

**Patches**

* Fixed an issue which prevented you from using the **Merge selected lines** workflow option. (NEO-48488)
* Fixed an issue which prevented the **Success** delivery indicator from being updated correctly when using Adobe Campaign Enhanced MTA. (NEO-50462)
* Fixed an issue when resetting content approval in an email delivery, which prevented you from reapproving. (NEO-44259)
* Fixed an issue which could prevent the **Delivery approval** button from being displayed. (NEO-47547)
* Fixed a performance issue in the HTML tab of a delivery which could occur for large HTML code. (NEO-47440)
* Fixed an issue which impacted the delivery log status updates on the MID instance, when the `FeatureFlag_GZIP_Compression` option was enabled. (NEO-49183)
* Fixed an issue which prevented you from sending iOS mobile app notifications from an execution instance while using token-based authentication. (NEO-45961)
* Fixed an issue with the **Refresh for deliverability** workflow (deliverabilityUpdate) which got stuck when having too many broadlogs to synchronize. (NEO-48287)
* Fixed an events type issue which blocked the **Message Center synchronization** (mcSynch) workflow.
* Fixed an issue which could lead to an error when adding the **Recipients who have opened**  (estimatedRecipientOpen) indicator in the additional data of a **Query** workflow activity. (NEO-46665)
* Fixed an issue with the **Billing** workflow which failed when having Message Center Control and Execution packages installed on the same instance. (NEO-47674)
* Fixed an issue with the **Billing** workflow which failed when having tables with the primary key defined as a string instead of an integer. (NEO-46254)
* Fixed an issue with heatmap filters when the workflow name was too long. (NEO-46301)
* Fixed an issue introduced in 7.3.1 on Snowflake FDA connector which led to records being dropped when using "0 or 1 cardinality simple join" during enrichment. (NEO-48737)
* Fixed an issue with Snowflake FFDA when using the sorting parameter in a **Split** workflow activity. (NEO-45899)
* Fixed an issue which could prevent you from saving external account configuration. The external account is now automatically saved after the connection test, for connectors with parser capability (Snowflake & Google BigQuery). (NEO-47636)
* Fixed an issue which prevented you from inserting a Time datatype in a **Data Update** workflow activity on MSSQL. (NEO-47763)
* Fixed an issue which led to the MTA process crashing when the engine's timezone was not set (specific to MSSQL). (NEO-46619)
* Fixed an issue with HTML file import when image nodes (img) contained URLs with personalization fields. (NEO-48396)
* Fixed an HTTP 500 error when trying to connect to an instance where the `limit` node was not configured in the serverConf.xml file.
* Fixed an issue which could lead to a "Character set mismatch" error when using certain functions such as `to_nclob` with an Oracle unicode database where NChar was not enabled. (NEO-49361)
* Fixed an issue that led to an error when a user with read access rights on the nmsDeliveryMapping folder tried to run a campaign or workflow. (NEO-48230)
* Fixed an issue which prevented the `JSPContext.sqlExecWithOneParam` function from working. (NEO-50066)
* Fixed various redirection errors. (NEO-50030)
