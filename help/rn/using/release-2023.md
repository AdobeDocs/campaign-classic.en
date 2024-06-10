---
product: campaign
title: Campaign Classic 2023 releases
description: Learn more about Campaign Classic 2023 releases
feature: Release Notes
role: User
level: Beginner
exl-id: 8ed11e96-9f23-4e2e-bae2-25c51cfb549a
---
# 2023 releases{#release-2023}

## Release 7.3.5 - Build 9368 {#release-7-3-5}

[!BADGE Limited Availability]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Limited Availability"}

_December 5, 2023_

### Security enhancements {#release-7-3-5-security}


* With Campaign Classic v7.3.5, the authentication process has been improved and secured. Technical operators should now use Adobe Identity Management System (IMS) to connect to Campaign. Learn how to migrate your existing technical account(s) in [this technote](../../technotes/using/ims-migration.md).
  
* In addition, as part of the effort to reinforce security and authentication process, Adobe Campaign highly recommends to migrate end user authentication mode from the login/password native authentication to Adobe Identity Management System (IMS). Learn how to migrate your operators in [this technote](../../technotes/using/migrate-users-to-ims.md).

* Now, when a web form has the **Pending publication** status, it does not become automatically live. To prevent security issues, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Patches {#release-7-3-5-patches}

* Fixed an issue when using data from a Google Big Query database and updating data in an Oracle database: all keys were set to `0` in the workflow temporary table. (NEO-65091)
* Fixed an issue which was causing a workflow execution to fail when two queries on a Google Big Query database were combined in a **Union** workflow activity. (NEO-63705)
* Fixed an issue which was requesting the user to re-authenticate when clicking the `Back` button in a Campaign report. (NEO-65087)
* Fixed an error in the Database Cleanup workflow which was happening when a delivery was deleted before its delivery proofs. (NEO-48114)
* Fixed an issue while connecting to the Client Console: recent updates on TLS verification were leading to connection error. (NEO-50488)
* Fixed an issue with the HTTP Proxy authentication after Campaign postupgrade to 7.3.1. HTTP requests in Campaign workflows were failing with `error 407 – proxy auth required is returned`. (NEO-49624)
* Fixed an intermitent failure with GPG decryption in **Script** workflow activities. The associated error message was: `gpg: decryption failed: No secret key`. (NEO-50257)
<!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->




## Release 7.3.4 - Build 9364 {#release-7-3-4}

[!BADGE Limited Availability]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Limited Availability"}


>[!CAUTION]
>
>Client Console upgrade is mandatory. Learn how to upgrade your Client Console in this [page](../../installation/using/installing-the-client-console.md).
>
>If you are using [Campaign - Microsoft Dynamics CRM Connector](../../platform/using/crm-connectors.md), you must upgrade both your marketing and your mid-sourcing servers with this new build.

_September 7, 2023_

### Security enhancements {#release-7-3-4-security}

* Security has been improved in IMS APIs. Client-sensitive information (i.e. access tokens) has been removed from URL parameters. These credentials are now sent in the post data or authorization header, ensuring a more secure communication process. (NEO-63045)
* Security has been improved in web apps to prevent DDOS attacks. (NEO-50757)
* Security has been enhanced to prevent PII data from being exposed in the web logs errors. (NEO-46827)
* Security has been optimized to prevent the security token from being included in the Campaign home page URL. (NEO-38519)

### Compatibility updates  {#release-7-3-4-compat}

* Tomcat has been updated to version 8.5.91
* The libexpat library has been updated to 2.5.0 to improve security. (NEO-51023)

### Improvements {#release-7-3-4-improvements}

* The MaxWorkingSetMb parameter in the server configuration file (serverConf.xml) has been modified to optimize memory allocation for deliveries. (NEO-49204)
* The BigQuery external account has been enhanced with new options used to setup GCloud SDK. (NEO-63879) [Read more](../../installation/using/configure-fda-google-big-query.md#google-external)
* A new `cusHeader` section has been added in the server configuration file (serverConf.xml). It allows you to add custom headers when uploading a file from an external server. (NEO-58339) [Read more](../../installation/using/the-server-configuration-file.md#cusheaders).
* The tracking log management has been improved to avoid negative IDs for lastMsgId. It has been changed from int32 to int64. (NEO-52290)
* The Mid-sourcing (delivery statistics) workflow has been added out-of-the-box. This new workflow synchronizes delivery statistic data (nms:deliveryStat) from the mid to the marketing instance. (NEO-36802)

### Patches {#release-7-3-4-patches}

* Fixed an issue which could occur when a service request was made prior to IMS login, if the service request call authentication was using a service token. (NEO-64903)
* Fixed a regression issue which could lead to scrolling issues when using the Digital Content Editor. (NEO-64671, NEO-59256)
* Fixed a regression issue when pasting content from Excel to the Digital Content Editor. (NEO-63287)
* Fixed an issue which could prevent webapps from being correctly displayed in v5 compatibility mode. (NEO-63174)
* Fixed an issue which prevented non-admin operators from sending webAnalytics deliveries. (NEO-62750)
* Fixed an issue to prevent browsers from adding extra spaces when using conditional content in a delivery. (NEO-62132)
* Fixed a regression issue which prevented the active contact calculation from correctly working in the Billing workflow when using target schemas associated with multiple log schemas. (NEO-61468)
* Fixed an issue which could lead to an error and prevent you from scrolling when editing the content of a delivery. (NEO-61364)
* Fixed an issue which caused a popup window to open when clicking on an image in the email content editor. (NEO-60752)
* Fixed an issue which could lead to special characters in the HTML content of a delivery being incorrectly encoded in several browsers. (NEO-60081)
* Fixed a synchronization issue which could occur when using the inSMS workflow activity. (NEO-59544)
* Fixed an issue when using the Big Query connector with timestamp or datetime fields. (NEO-59502, NEO-49768)
* Fixed an issue which prevented you from using cumulative delivery reports. (NEO-59211)
* Fixed an issue which could lead to errors when sharing audiences with People Core Service. (NEO-58637)
* Fixed an issue when displaying the mirror page of a delivery. (NEO-58325)
* Fixed an issue which prevented the XtkLibrary.Right() xtk expression from working. (NEO-57870)
* Fixed an issue which led the style attribute of the body tag to be changed when uploading an image in the Digital Content Editor. (NEO-57697)
* Fixed an issue with special characters when performing batch exports with the CRM connector activity. (NEO-54300)
* Fixed an issue which prevented bulk loading from working with "string" data types when using a Data loading activity and the Big Query connector. (NEO-53748)
* Fixed a cache key issue which could lead to offer rendering issues. (NEO-51516, NEO-49995)
* Fixed an issue which could lead to a validation error when sending a direct mail delivery using targetMapping with approvals. (NEO-50758)
* Fixed a query management issue which could impact delivery performance. (NEO-49991)
* Fixed an issue, when using external accounts in campaign workflow delivery activities, which could lead to external account configuration issues. (NEO-49959)
* Fixed a performance issue when sending push notifications. (NEO-49953)
Fixed an issue which could cause Japanese characters to be incorrectly displayed when exporting reports (NEO-49308).
* Fixed an issue which caused the Tomcat error report to display too much error details. (NEO-49029)
* Fixed an issue which could lead to a delivery error when using a large number of offers. (NEO-48807)
* Fixed an issue which could prevent the **Update data** workflow activity from working correctly. (NEO-48140)
* Fixed an issue which could prevent click tracking data from being synchronized for deliveries using an external account different than email.(NEO-47277)
* Fixed an issue which could prevent real-time tracking logs from being synchronized on Message Center marketing instance. (NEO-42540)
* Fixed an issue which prevented the workspace prefix from being displayed in the discovery window of a schema, for Snowflake database tables. (NEO-40297)
* Fixed an issue which prevented `<img-amp>` tags from working in email content. (NEO-38685)
* Fixed an issue which could cause the Message Center archiving workflow to fail when using an HTTP relay. (NEO-33783)
* Fixed an issue which could cause font name and size erros in the email content editor. (NEO-61342)

## Release 7.3.3 - Build 9359 {#release-7-3-3}

[!BADGE Limited Availability]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Limited Availability"}

>[!AVAILABILITY]
>
>A specific Campaign v7.3.3.IMS patch upgrade is available for this version - if no other patch has been applied to your environment. It brings [Adobe Identity Management System (IMS) security updates coming with v7.3.5](#release-7-3-5-security) to existing v7.3.3 environments.


_March 20, 2023_


### Security enhancement {#release-7-3-3-security}

* To optimize security, Tomcat has been updated from version 8.5.81 to 8.5.85. (NEO-56936)



### Improvements {#release-7-3-3-improvements}

* The Billing workflow has been improved to optimize performance. (NEO-47658)
* The tracking workflow has been improved to optimize performance in case of high delivery size. (NEO-45064)
* Tracking management has been improved to fix possible issues with dynamic parameters in URLs. Tracking management v3 now handles ajax type URLs (with parameters after a '#') and prevents third-party tools from modifying tracking URLs. To apply this change, you need to contact Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>Client Console upgrade is mandatory. Learn how to upgrade your Client Console in this [page](../../installation/using/installing-the-client-console.md).

### Patches {#release-7-3-3-patches}

* Fixed an issue which could prevent iOS proof push notifications from being sent from the control instance (Transactional Messaging context). (NEO-54713)
* Fixed an issue which could prevent you from scrolling in the **Edit** tab of the Digital Content Editor (DCE). (NEO-54474)
* Fixed an issue, when two enrichment activities were using the same name identifier in their linking, which led the second enrichment activity to use the links of the first one. (NEO-48851)

## Release 7.3.2 - Build 9356 {#release-7-3-2}

[!BADGE Limited Availability]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Limited Availability"}


>[!AVAILABILITY]
>
>A specific Campaign v7.3.2.IMS patch upgrade is available for this version - if no other patch has been applied to your environment. It brings [Adobe Identity Management System (IMS) security updates coming with v7.3.5](#release-7-3-5-security) to existing v7.3.3 environments.

_November 21, 2022_

### Compatibility updates {#release-7-3-2-compat}

* Adobe Campaign is now compatible with PostgreSQL 14. For more information, refer to this [technote](../../technotes/using/tech-stack-upgrade.md).

* Following the end of life of Microsoft Internet Explorer 11, the HTML rendering engine for dashboards in the client console is now using Edge Chromium. (NEO-20741)

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md#RDBMSservers).

>[!CAUTION]
>
>Client Console upgrade is mandatory. Learn how to upgrade your Client Console in this [page](../../installation/using/installing-the-client-console.md).

### Improvements {#release-7-3-2-improvements}

* The Google BigQuery connector now fully supports boolean fields. (NEO-49181)
* You can now configure the IMS cookies validity duration in the `Configuration for the redirection service` section of the serverConf.xml file. This applies to the following cookies: `uuid230`, `nllastdelid` and `AMCV_` (NEO-42541)
* The IP can now be hidden in the "/r/test" request by setting `showSourceIP` to false in the redirection node of the serverConf.xml file. [Read more](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

### Deprecated features  {#release-7-3-2-deprecated}

* Social Marketing with Facebook is now deprecated. You can use X (formerly known as Twitter) integration to post on social media, or work with Adobe to create a custom channel.
* ACS Connector (Prime offering) is now deprecated. You can use Campaign export/import capabilities to extract and inject data in both products.

Learn more in the [Deprecated and removed features page](deprecated-features.md).

### Other changes  {#release-7-3-2-other}

<!--* Web logs have been improved: `logonEscalation` warnings are now only displayed for users with admin privileges. (NEO-47167)-->
* To avoid errors, the **Collect data for Heatmap service** (collectDataHeatMapService) workflow is now stopped by default. (NEO-33959)
* Various improvements were implemented to optimize CPU usage for the campaigns dashboard. (NEO-46417)
* To prevent crashes, the loadLibraryDebug JS method has been removed. (NEO-46968)
* The remaining references to the log4j library have been removed from the Campaign installation on Windows. (NEO-44851)

### Patches {#release-7-3-2-patches}

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
