---
title: Latest Release
description: Latest Campaign Classic Release
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
---

# Latest Release{#latest-release}

# Release 20.3{#release-20-3}

## ![](assets/do-not-localize/blue_2.png) Release 20.3.1 - Build XXX {#release-20-3-1-build-XXX}

_October 27, 2020_

**What's new?**

<table> 
<thead>
<tr> 
<th> <strong>iOS push notification improvements</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>You can now choose between two authentication modes for iOS in Campaign Classic:</p>
<ul> 
<li><p>Certificate-based authentication using p12 key.</p></li> 
<li><p>Token-based authentication using p8 certificate.</p></li>
</ul>
<p>For more information, refer to the <a href=../../delivery/using/configuring-the-mobile-application.md>detailed documentation</a>.</p>
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
<td> <p>Android push notifications have been improved to support FCM HTTP/V1 API for Android push channel authentication. </p>
<p>With the new supported API version, you can now send FCM Notification Messages which provides enhanced rich push messaging capabilities.</p>
<p>For more information, refer to the <a href=../../delivery/using/configuring-the-mobile-application-android.md>detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Security enhancements**

* Secure loading of libraries: Campaign now prevents unnecessary DLLs from loading while charging Campaign Client (nlclient) to protect from DLL preloading attacks. [Learn more](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Fixed two Server-Side Request Forgery (SSRF) issues, one in the exportReport.jsp file and one within the usage of the CaptchaValidate() JavaScript function, that could be vulnerabilities for attackers to probe internal network services available to the server.
* Fixed an issue that occurred while handling GDPR privacy requests that prevented records from being deleted from custom tables with a second-level relationship to the Recipient table. (NEO-25967)
* Fixed a security issue using API calls made by non-admin users when trying to synchronize Adobe Experience Manager templates.

**Compatibility updates and deprecated features**

The following systems are now supported with Campaign:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

Starting 20.3, the demdex domain used to import and export audiences to the Adobe Experience Cloud is deprecated. If you are using the demdex domain for your import/export external accounts, you need to adapt your implementation accordingly. [Learn more](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

**Improvements**

* Several improvements have been made to the **Client console**:
   * To prevent incompatibility with some internet security GPO rules restrictions, the Campaign client console logon screen has been replaced by a built-in standard Windows form. 
   * Fixed an issue when copy/pasting activities in a workflow using 64-bits Client console. (NEO-27635) 
   * In the **About** menu, information has been added to distinguish 64 and 32 bits consoles. 
* In delivery properties, the **[!UICONTROL Archive emails]** option has been renamed **[!UICONTROL Email BCC]** for a better user experience.
* The workflow identifier is now displayed in the logs when resuming a workflow, which allows you to identify better which workflow was resumed.
* Triggers integration authentication originally based on oAUTH authentication setup to access pipeline has now been changed and moved to Adobe I/O. 
* In the **Update event status** technical workflow, the sizing of the **sumQueueTime**, **sumSuccessDeliveryTime** and **sumSuccessDeliveryQueueTime** destination fields was changed from 32 to 64 bits for the Update delivery stats activity. This is to match the sizing of the incoming corresponding fields in the **Delivery statistics** activity and therefore prevent the **Update delivery stats** activity from failing. (NEO-11557)
* A new permanent cookie has been introduced: nllastdelid. This cookie (other than UUID230) will store deliveryId. When session cookie is not present, broadlog information would be taken from the deliveryId present in this cookie.
This change fixes an issue which occurred when the browser session was over: the session cookie containing deliveryId and broadlogId got deleted. Without deliveryId, broadlog information could not be found and the tracking table information would be missing in case of permanent tracking (last delivery).
Learn more about cookies in this [section]() > link to https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/starting-with-adobe-campaign/privacy-and-recommendations.html#cookies"

**Other changes**
* In delivery properties, the **[!UICONTROL Archive emails]** option has been renamed **[!UICONTROL Email BCC]** for a better user experience.

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
* Windows NT authentication has been removed from the available authentication methods when configuring a new database with a Microsoft SQL Server.
* Fixed an issue when using the Snowflake FDA connector. A user with the Snowflake FDA access name rights could not execute a query on a Snowflake schema. An error of the type "Password not found" was displayed in the logs. (NEO-23851)
* Fixed an issue when using an FDA connector which happened when the linked FDA schema name was a substring of an element name of the current schema. This occurred, for example, if the FDA schema was "cust" and one of the elements within the Recipient schema was "customer". When fetching the column inside the "customer" element and adding a column from the "cust" FDA schema, the value for the local column was missing. (NEO-20193)
* The database cleanup workflow has been optimized for Teradata in order to improve performance. (NEO-19959)
* Fixed an issue in workflows when fetching records from an external database and inserting them in the Campaign database. (NEO-26359)
* Improved the error message displayed when inserting an image from Adobe Target and the tenant name was empty in the external account.
* Fixed an issue in the **Message Center Event History** report that caused script errors when trying to apply filters and made the filter by a date range impossible. (NEO-23365)
* Fixed an interference issue between the **Campaign jobs** (operationMgt) and **Preview** (forecasting) technical workflows. This occurred when scheduled deliveries stayed in "Target Ready" or "Ready to be delivered" status. (NEO-20819)
* Fixed an XML parsing issue when the XML identifier was not be present in mdata field in xtkOperator. It was causing postupgrade failure. (NEO-26113)
* Fixed an issue when using the **File Transfer** activity linked to an Azure external account encrypted in SSL where the connection was made with HTTP instead of HTTPS. (NEO-26720)
* Fixed an issue for MSSQL database where an error could occur with the up_updatestats procedure during the clean up workflow.
* Fixed a crash which occurred during the web process shutdown if Interaction requests were still being processed. (NEO-26447)
* When using relative path for SFTP,  `~/` will not be added automatically anymore. If you need to use SFTP, you can add `~/` to your path manually but we recommend using absolute path.
* Fixed an issue where the **NoNull** function in Oracle DB was not working anymore after upgrade 9032. (NEO-26488)
* Fixed an issue where the tracking workflow was failing after upgrade 9171 if the LINEV2 package was installed without the Message Center package.
* Fixed a scalability issue that prevented the connection pool from being increased to the desired number of connections because the database connection string for the attribute 'APP' ended up getting an invalid value. (NEO-25105)
* Fixed an issue at the proxy configuration level that prevented you from logging into Adobe Campaign after the latest Windows 10 update. (NEO-27813)
* Fixed an issue that made unwanted URLs visible in the delivered emails after importing HTML templates containing tracking links. (NEO-25909)
* Fixed an issue that caused the server to crash when displaying the target data of the remainder from a **Split** activity in a workflow.
* Fixed a server crash issue by preventing memory corruption when cleaning the expression parser. (NEO-26856)
* Improved high volume delivery throughout performance via the deliverability server.
* Fixed an issue in the enrichment activity where non-admin users defined instance variables. (NEO-25653) 