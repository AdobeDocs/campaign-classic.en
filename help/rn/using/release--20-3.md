---
solution: Campaign Classic
product: campaign
title: Campaign 20.3 release notes
description: Release notes for Campaign 20.3
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: e927b7fc-95cd-4e08-bab7-ceeb6e67c265
---
# Release 20.3{#release-20-3}

## ![](assets/do-not-localize/red_2.png) Release 20.3.3 - Build 9234 {#release-20-3-3-build-9234}

_January 11, 2021_

* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)
* Fixed a regression issue related to the broadlog generation process that could cause the MTA process to crash.

## ![](assets/do-not-localize/red_2.png) Release 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_October 27, 2020_

>[!CAUTION]
>
> * This release comes with a new connection protocol: if you are connecting to Campaign through Adobe Identity Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**.
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 
> * If you are using the Experience Cloud Triggers integration through oAuth authentication, you need to move to Adobe I/O as described [in this page](../../integrations/using/configuring-adobe-io.md). Legacy oAuth authentication mode with Campaign will be retired on **November 30, 2021**.

**What's new?**

<table> 
<thead>
<tr> 
<th> <strong>iOS push notification improvements</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>When integrating your mobile app with Campaign, you need to secure your communication with Apple Push Notification service (APNs). You can use certificate-based or token-based authentication.
</p>
<p>These two authentication modes are now available for iOS mobile apps in Campaign Classic:
</p>
<ul> 
<li><p>Token-based authentication (recommended): this authentication mode is based on a .p8 file. This authentication mode is faster as each request to APNs contains the token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Learn more</a></p></li>
<li><p>Certificate-based authentication: this authentication mode is based on a .p12 file. For every app, a separate certificate is required. This certificate is delivered by Apple through your developer account. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Learn more</a></p></li> 
</ul>
<p>Learn how to select the authentication mode in Campaign in the <a href="../../delivery/using/configuring-the-mobile-application.md">detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Android push notification improvements</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Android push notifications</a> have been improved to support FCM HTTP v1 API for Android push channel authentication. </p>
<p>With the new supported API version, you can now send FCM Notification Messages which provides enhanced rich push messaging capabilities. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Learn more</a></p> 
<p>Learn how to configure FCM HTTP v1 API for Android in Adobe Campaign in <a href="../../delivery/using/configuring-the-mobile-application-android.md">this section</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Security enhancements**

* Secure loading of libraries: In order to protect from DLL preloading attacks, Campaign now loads Windows DLLs only from the Windows default system DLL path while loading the Campaign Client (nlclient). [Learn more](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) attacks. (NEO-25661)
* Fixed an issue that occurred while handling GDPR privacy requests that prevented records from being deleted from custom tables with a second-level relationship to the Recipient table. (NEO-25967)
* Fixed a security issue using API calls made by non-admin users when trying to synchronize Adobe Experience Manager templates. (NEO-23487)

**Compatibility updates**

The following systems are now supported with Campaign:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Deprecated features**

The following features are deprecated in 20.3:

* The demdex domain used to import and export audiences to the Adobe Experience Cloud is deprecated. If you are using the demdex domain for your import/export external accounts, you need to adapt your implementation accordingly. [Learn more](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Triggers integration authentication originally based on oAUTH authentication setup to access pipeline has now been changed and moved to Adobe I/O. [Learn more](../../integrations/using/configuring-adobe-io.md)

Learn more in the [Deprecated and removed features page](../../rn/using/deprecated-features.md).

**Improvements**

* Several improvements have been made to the **Client console**:
   * The connection protocol has been updated to follow the new IMS authentication mechanism. Server and client console upgrade is mandatory to be able to connect after June 30, 2021.
   * To prevent incompatibility with some internet security GPO rules restrictions, the Campaign client console logon screen has been replaced by a built-in standard Windows form. 
   * Fixed an issue when copy/pasting activities in a workflow using 64-bits Client console. (NEO-27635) 
   * In the **About** menu, information has been added to distinguish 64 and 32 bits consoles. 
* The workflow identifier is now displayed in the logs when resuming a workflow, which allows you to identify better which workflow was resumed.
* A new permanent cookie has been introduced: nllastdelid. This cookie (other than UUID230) will store deliveryId. When session cookie is not present, broadlog information would be taken from the deliveryId present in this cookie.
This change fixes an issue which occurred when the browser session was over: the session cookie containing deliveryId and broadlogId got deleted. Without deliveryId, broadlog information could not be found and the tracking table information would be missing in case of permanent tracking (last delivery).
Learn more about cookies in [this section](../../platform/using/privacy-and-recommendations.md#cookies).
* Improved high volume delivery throughput performance with deliverability server by restarting the MTA process before delivery sending.

**Other changes**

* When using relative path for SFTP, `~/` characters are no longer automatically added. If needed, you can add `~/` characters to your path manually but Adobe recommends using an **absolute path**.
* Windows NT authentication has been removed from the available authentication methods when configuring a new database with a Microsoft SQL Server. [Read more](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* The database cleanup workflow has been optimized for Teradata in order to improve performance. (NEO-19959)
* Improved the error message displayed when inserting an image from Adobe Target and the tenant name was empty in the external account.
* In delivery properties, the **[!UICONTROL Archive emails]** option has been renamed **[!UICONTROL Email BCC]**.
* To improve robustness, selectAll queries with invalid nodes are now rejected. If you need to disable the check and get back to the previous behavior, you can set the XtkSecurity_Disable_QueryCheck to 0.

**Technical evolutions**

Tomcat has been updated from version 7 (7.0.103) to version 8 (8.5.57).

The `tomcat-7` directory is replaced with a `tomcat-8` directory.

On windows, _iis_neolane_setup.vbs_ and _apache_neolane.conf_ are now installed in the `conf` directory (instead of `tomcat-7/conf` previously).

On linux, _apache_neolane.conf_ is now installed in the `conf` directory.

**Patches**

* Fixed an issue which could prevent delivery statistics from being recomputed.
* Fixed an issue which displayed an error message when uploading a CSV file when using Campaign Classic 9080 build connected to a server using an older build. (NEO-23218)
* Fixed an issue that could display an error message when configuring Microsoft Dynamics CRM wizard for an external account. This was due to a compatibility issue with the latest MS Dynamics CRM API version. (NEO-24528)
* Fixed an issue that prevented you from exporting look up-type records (meaning data made up of foreign key records connected with other tables) from Campaign Classic to Microsoft Dynamics using the CRM connector. (NEO-23864)
* Fixed an issue that could prevent Microsoft Dynamics data from being fetched if the **Automatic index** option was enabled in the CRM connector. (NEO-25981)
* Fixed an issue with IMS authentication that could leave connections opened even if they were ended. Terminated connections will now be automatically closed as soon as they are ended in order to avoid accumulating connections and consuming system resources. (NEO-25996)
* Fixed an issue that showed no error message when the synchronization of Adobe Experience Manager content failed for a delivery, due to a misconfiguration of the external account (incorrect account or password). A message now displays in case of failure, allowing you to identify more easily the issue. (NEO-25586)
* Fixed an issue that occurred when selecting the **Update** operation type in the **Update data** activity. If the data to update was incorrect, the workflow would be in error and fail. In case of incorrect data, the workflow will not fail, and the records will be stored into a **Rejects** outbound transition. (NEO-23794)
* Fixed an issue that could prevent workflows containing sub-workflows from working. (NEO-24036)
* Fixed an issue when editing a campaign template description that prevented the **Save** button from displaying when copy-pasting symbols like, for example, Japanese characters. (NEO-27071)
* Fixed an issue which could prevent you from changing the tracking server in the instance configuration wizard.
* Fixed an issue which prevented the description of a campaign or campaign template from being saved when clicking outside of the window before clicking the **Save** button. (NEO-27449)
* Fixed an issue that could prevent the **Number of active billing profiles** (billingActiveContactCount) technical workflow from working. This could happen if a link had been performed on a calculated field in a schema extension. Large amount of data was created, which could lead the database to run out of temporary space. (NEO-24062)
* Fixed an issue with the **Data loading (file)** activity, which could prevent you from importing Japanese characters from txt and csv files if they were positioned at the end of the file. (NEO-24957)
* Fixed an issue with continuous deliveries which could prevent the **Analysis Started** and **Analysis Completed** fields from being populated correctly. (NEO-20755)
* Fixed an issue that could display an error message when trying to preview SMS messages after a query on another schema than **Recipient** (nms:recipient). (NEO-27517)
* Fixed an issue when using the Snowflake FDA connector. A user with the Snowflake FDA access name rights could not execute a query on a Snowflake schema. An error of the type "Password not found" was displayed in the logs. (NEO-23851)
* Fixed an issue when using an FDA connector which happened when the linked FDA schema name was a substring of an element name of the current schema. This occurred, for example, if the FDA schema was "cust" and one of the elements within the Recipient schema was "customer". When fetching the column inside the "customer" element and adding a column from the "cust" FDA schema, the value for the local column was missing. (NEO-20193)
* Fixed an issue in workflows when fetching records from an external database and inserting them in the Campaign database. (NEO-26359)
* Fixed an issue in the **Update event status** technical workflow: to match the sizing of the incoming corresponding fields in the **Delivery statistics** activity, the sizing of three destination fields in the **Update delivery stats** activity was changed from 32 to 64 bits. (NEO-11557) Learn more about the **Update event status** workflow in [this section](../../workflow/using/about-technical-workflows.md).
* Fixed an issue in the **Message Center Event History** report that caused script errors when trying to apply filters and made the filter by a date range impossible. (NEO-23365)
* Fixed an interference issue between the **Campaign jobs** (operationMgt) and **Preview** (forecasting) technical workflows. This occurred when scheduled deliveries stayed in "Target Ready" or "Ready to be delivered" status. (NEO-20819)
* Fixed an XML parsing issue when the XML identifier was not be present in mdata field in xtkOperator. It was causing postupgrade failure. (NEO-26113)
* Fixed an issue when using the **File Transfer** activity linked to an Azure external account encrypted in SSL where the connection was made with HTTP instead of HTTPS. (NEO-26720)
* Fixed an issue for MSSQL database where an error could occur with the up_updatestats procedure during the clean up workflow.
* Fixed a crash which occurred during the web process shutdown if Interaction requests were still being processed. (NEO-26447)
* Fixed an issue where the **NoNull** function in Oracle DB was not working anymore after upgrade 9032. (NEO-26488)
* Fixed an issue where the tracking workflow was failing after upgrade 9171 if the LINEV2 package was installed without the Message Center package.
* Fixed a scalability issue that prevented the connection pool from being increased to the desired number of connections because the database connection string for the attribute 'APP' ended up getting an invalid value. (NEO-25105)
* Fixed an issue at the proxy configuration level that prevented you from logging into Adobe Campaign after the latest Windows 10 update. (NEO-27813)
* Fixed an issue that made unwanted URLs visible in the delivered emails after importing HTML templates containing tracking links. (NEO-25909)
* Fixed an issue that caused the server to crash when displaying the target data of the remainder from a **Split** activity in a workflow.
* Fixed a server crash issue by preventing memory corruption when cleaning the expression parser. (NEO-26856)
* Fixed an issue in the enrichment activity where non-admin users defined instance variables. (NEO-25653)
