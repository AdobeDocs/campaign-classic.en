---
product: campaign
title: 2020 releases
description: Learn more about Campaign Classic 2020 releases
feature: Overview
role: User
level: Beginner
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
---
# 2020 releases{#release-2020}

![](../../assets/v7-only.svg)


## Release 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Release 20.3.3 - Build 9234 {#release-20-3-3-build-9234}

_January 11, 2021_

* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)
* Fixed a regression issue related to the broadlog generation process that could cause the MTA process to crash.

### ![](assets/do-not-localize/red_2.png) Release 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_October 27, 2020_

>[!CAUTION]
>
> * This release comes with a new connection protocol: if you are connecting to Campaign through Adobe Identity Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**. [Learn more](../../technotes/using/ims-updates.md)
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 
> * If you are using the Experience Cloud Triggers integration through oAuth authentication, you need to move to Adobe I/O as described [in this page](../../integrations/using/configuring-adobe-io.md). Legacy oAuth authentication mode with Campaign [has been retired](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) on **September 2021**. Hosted environments benefit from an extension until  **Febuary 23, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to Febuary 2022. You must provide [the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) to Adobe.

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
* Fixed a regression that could block the workflow data export to an FDA database (Teradata, Snowflake).

## Release 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Release 20.2.5 - Build 9188 {#release-20-2-5-build-9188}

_April 15, 2021_

* Fixed a client console regression which caused persistent error messages on the IMS connection screen. (NEO-34821)

**Console upgrade only is mandatory. No server upgrade is required.**

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_March 31, 2021_

**Improvements**

* An improvement has been made to prevent crashes on invalid soap calls. This could cause the instance to stop working when trying to run specific complex queries. (NEO-28796, NEO-30553)
* Fixed a regression which prevented SMS deliveries with TLS from being sent due to the hostname verification. (NEO-29581)
* Fixed an issue which prevented signed tracking links from working on some email clients. (NEO-28414, NEO-29615)
* Fixed a tracking id sequence when using webApp tracking tags which could cause conflicts with duplicate IDs. (NEO-27931)
* Fixed an issue which caused running workflows to be stopped by the daily wfserver restart. (NEO-30047)
* Fixed a security issue using API calls made by non-admin users when trying to synchronize Adobe Experience Manager templates. (NEO-32389, NEO-23487)
* Fixed an issue causing the console to crash when closing a delivery dialog on a delivery created with from a template. (NEO-31547)
* Fixed an issue which occurred when creating and saving a delivery within the **Targeting & Workflow** tab of a campaign: the preview would fail with the following error. (NEO-29440)
* Fixed an issue with Tomcat 8.5 sending invalid answers which caused errors in Transactional Messaging logs. (NEO-30858)
* Fixed a regression issue causing memory corruption in external thread management and impacting performance.
* Fixed an issue which could cause the Billing workflow to fail when using a custom target mapping. The primary key of the custom schema is stored in the ‘sourceId’ column which only allowed integer values. It now allows integer as well as string values. (NEO-25914, NEO-28146)
* Fixed a regression preventing the usage of some components of the console, such as the date picker and images management in deliveries. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Release 20.2.4 - Build 9187 {#release-20-2-4-build-9187}

_April 15, 2021_

* Fixed a client console regression which caused persistent error messages on the IMS connection screen. (NEO-34821)
* Fixed a regression preventing the usage of some components of the console, such as the date picker and images management in deliveries. (NEO-31453, NEO-31454)

**Console upgrade only is mandatory. No server upgrade is required.** 

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_December 22, 2020_

>[!CAUTION]
>
> * This release comes with a new connection protocol: if you are connecting to Campaign through Adobe Identity Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**.  [Learn more](../../technotes/using/ims-updates.md)
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 
> * If you are using the Experience Cloud Triggers integration through oAuth authentication, you need to move to Adobe I/O as described [in this page](../../integrations/using/configuring-adobe-io.md). Legacy oAuth authentication mode with Campaign [has been retired](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) on **September 2021**. Hosted environments benefit from an extension until  **Febuary 23, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to Febuary 2022. You must provide [the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) to Adobe.

**Improvements**

* The connection protocol has been updated to follow the new IMS authentication mechanism. 
* Triggers integration authentication originally based on oAUTH authentication setup to access pipeline has been changed and moved to Adobe I/O. [Learn more](../../integrations/using/configuring-adobe-io.md)
* Following the [end of support for iOS APNs legacy binary protocol](https://developer.apple.com/news/?id=c88acm2b), all instances using this protocol are updated to HTTP/2 protocol during postupgrade.
* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)
* Fixed an issue causing the deactivation of the SMPP connector after a connection error, preventing other SMS deliveries from being sent and leading to performance issues. (NEO-28609)
* Fixed a server crash issue by preventing memory corruption when cleaning the expression parser. (NEO-26856)
* Fixed an issue that caused the server to crash when displaying the target data of the remainder from a **Split** activity in a workflow.
* Fixed an issue that could display an error message when trying to preview SMS messages after a query on another schema than **Recipient** (nms:recipient). (NEO-27517)
* Fixed an issue when making an HTTPS connection request with the port number explicitly defined in the host name, the call failed with a certificate error. (NEO-29146)
* Fixed an issue in POSIX thread management which generated large core dump files on the marketing instance. (NEO-28117, NEO-29281)
* Fixed issues which could cause the web process to crash when preparing deliveries or with recurring delivery preview. (NEO-27790, NEO-27517)
* Fixed an issue which caused deliveries or proof sending to fail when triggered by a non-admin operator. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **New Control Panel October release** with domain configuration using CNAMEs and new database monitoring capabilities. [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

### ![](assets/do-not-localize/red_2.png) Release 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_September 11, 2020_

* Fixed a regression causing delivery preparation to be blocked due to a single erroneous function on delivery part leading to memory overload. (NEO-27346)
* Fixed a postupgrade issue which turned off Apache and the web server before the web application republication. (NEO-27155)
* Fixed a regression on HTML template management leading to tracking URLs becoming visible due to a misinterpretation of tabs. (NEO-25909)
* Fixed an issue with the database cleanup workflow which could fail due to unmanaged data source. (NEO-23160, NEO-23364)
* The cleanup workflow now purges expired lists by batches of 100 instead of one by one.
* Fixed a regression which prevented you from modifying the internal name of an external account. (NEO-27323)
* Fixing a regression during postupgrade causing an incorrect start of nlserver (error logs).
* The update management for shared memory has been improved. The additional steps required in 20.2 are not needed anymore. 

### ![](assets/do-not-localize/red_2.png) Release 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_July 22, 2020_

* Fixed an issue which prevented tracking from working when the signature feature was disabled. (NEO-26411)
* Fixed an issue which led to unsigned links from personalized domains being blocked when they should be allowed. (NEO-25210)
* Fixed an issue which could prevent you from opening/clicking tracking URLs when using certain legacy versions of Outlook. (NEO-25688)
* Fixed an issue which led to mirror page URLs being incorrectly defined in email deliveries (due to improper ASCII character control). (NEO-26084)
* Fixed an issue with encoding URL management in the anti-phishing service. (NEO-25283)
* Fixed an issue which prevented the tracking of URLs using fragments in personalization parameters (anchor tags with pound-sign) from working. (NEO-25774)
* Fixed a tracking issue when using specific custom tracking formulas. (NEO-25277)
* Fixed an issue which prevented the tracking of "notification clicks" from working (iOS and Android push notifications). (NEO-25965)
* Fixed a regression impacting calculated fields in a workflow causing the workflow to fail. (NEO-25194)
* Fixed a regression which prevented the on-the-fly creation of web tracking URLs from working. (NEO-20999)
* Fixed a regression issue with out-of-the-box delivery reports which appeared truncated when exported to PDF. (NEO-25757)
* Fixed a crash issue in the deployment wizard.
* Fixed an issue which could prevent the Offer notification workflow from properly working after a postupgrade.
* The iOS HTTP2 connector has been improved (third-party updates and error management). (NEO-25904, NEO-25903)
* The jarsToSkip list in catalina.properties has been updated to remove the reference to a jar file that was no longer used (iOS notifications).
* Fixed an issue blocking delivery preparation after postupgrade.
* Following the switch to the [new sequence ID mechanism](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), all web applications that are updating the recipient table are republished during postupgrade.
* Fixed a potential XSS vulnerability in delivery content. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **New Control Panel June release** with Active profiles monitoring, Subdomain deliverability audit and GPG keys management. [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

### ![](assets/do-not-localize/red_2.png) Release 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_June 8, 2020_

**What's new?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Support of Emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>When designing a message in Campaign, you can now easily insert emoticons in the message body, using a dedicated button. They can also be added in the email subject line. You can customize the list of available emoticons in the interface.</p>
    <p>For more information about adding emoticons, refer to the <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">detailed documentation</a>. Learn how to customize the emoticon list <a href="../../delivery/using/customizing-emoticon-list.md">in this section</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>You can now connect your Campaign instance to your Azure Synapse external database. This connection is managed through a new external account.</p>
    <p>Azure Synapse is only available for Hybrid and On-premise environments. For more information, refer to the <a href="../../installation/using/configure-fda-synapse.md">detailed documentation</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Thailand and Brazil Privacy Laws</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Thailand’s Personal Data Protection Act (PDPA) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. </p>
   <p>Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective early 2021 for all companies collecting or processing personal data in Brazil.</p>
   <p>These regulations apply to Adobe Campaign customers who hold data for Data Subjects residing in these countries. In addition to the privacy capabilities already available in Campaign (including consent management, data retention settings, and user roles), we are taking this opportunity to include additional capabilities, to help facilitate your readiness for PDPA and LGPD:</p>
   <ul> 
     <li><p>Right to Access and Right to Delete: we are leveraging the capabilities that were added for GDPR and CCPA. <a href= https://helpx.adobe.com/campaign/kb/acc-privacy.html>Read more</a></p></li> 
     <li> <p>When creating a Privacy request using Campaign interface or API, you now select the <strong>Regulation</strong> type: PDPA, LGPD, GDPR, CCPA. <a href=https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests>Read more</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* Improved security on tracking links in email is enabled by default for all customers. An additional, enhanced security feature is available which can be enabled by reaching out to Customer Care. More details on the feature and steps for non-hosted customers to enable it can be found in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html). (NEO-24232)

* To optimize security, the MD5 hashing algorithm used to generate file names has been reinforced with sha256 for public file upload. (NEO-17044)

* To reinforce security against XSS attacks, client-side scripts are disabled when executing a mirror page. (NEO-17987)

* Fixed an issue which prevented the **Privacy Request Cleanup** technical workflow from deleting reconciliation data. (NEO-25168, NEO-21004)

* Fixed an issue with the **File Transfer** activity which prevented SFTP key based authentication from working on Debian 9. (NEO-23183)

**Compatibility enhancements**

The following systems are now supported with Campaign:
* Operating systems: Debian 10
* RDBMS: Oracle 18c and Oracle 19c
* FDA: Azure Synapse Analytics

Learn more in [Campaign Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

**Improvements**

* Transactional messaging has been improved for a better user experience. You can now unpublish a transactional message template, which deletes it from the execution instances. [Learn more](../../message-center/using/publishing-message-templates.md#template-unpublication).

* New options are available to set limitations when sending emails that include images or attachments. These guardrails can avoid performance issues, which is particularly useful with transactional messaging. [Read more](../../installation/using/configuring-campaign-options.md#delivery)

* The new **Prepare the delivery parts in the database** option enables to perform delivery preparation directly within the database, which can significantly accelerate the analysis. This option is only available for specific configurations. [Learn more](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* The performance of the [CRM Connector activity](../../workflow/using/crm-connector.md) for Microsoft Dynamics has been improved. (NEO-13303, NEO-12710)

* Shared memory version has been increased.

  >[!WARNING]
  >
  >This improvement requires an additional step after performing the upgrade. Refer to the **Technical evolutions** section below.

* The cleanup workflow has been enhanced. Orphaned worktables of all deleted workflows are now also deleted automatically by the cleanup workflow. [Learn more](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificates for iOS mobile applications with the iOS HTTP2 connector are now validated before sending push notifications, thus preventing deliveries from failing because of expired certificates. 

* The management of HTTP proxy connections has been improved. [Learn more](../../installation/using/file-res-management.md).

* New option in **[!UICONTROL Javascript Code]** and **[!UICONTROL Advanced Javascript Code]** workflow activities to stop execution after a limit. Default value is 1 hour. [Learn more](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Other changes**

* Legacy SMS connectors are now deprecated. Refer to the [Deprecated features page](../../rn/using/deprecated-features.md).

* You can no longer use your own Litmus account to provision and use Inbox rendering in Adobe Campaign. [Learn more](../../delivery/using/inbox-rendering.md).

* To better distinguish views from folders, the color of view names has been changed from dark blue to dark cyan. [Read more](../../platform/using/access-management-folders.md)

* Campaign Classic can now be connected to Microsoft Dynamics CRM accounts hosted in the UK, India and Canada regions. This applies to  Office 365 and On premise (Dynamics 2015) deployment types.

* Campaign now performs a TLS verification to check that the hostname of the server matches the hostname in the provided certificate.

* The Delivery and tracking statistics table now displays one entry per delivery for the SMS channel, instead of one entry per delivery recipient.  

* Added an error message in the log file to warn users when the downloaded file is larger than the disk space.

* The following functions are now available for the Snowflake connector: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Technical evolutions**

This new build updates shared memory and requires additional steps to perform the upgrade. As a Campaign administrator, you need to remove memory segments. These steps are mandatory, as old segments will prevent nlserver/nlsrvmod from starting.

On Windows, a system restart is needed.

On Debian/CentOs, shared memory deletion is needed. Here are the steps:

Before the upgrade, you need to follow these steps:

1. Stop the apache2 (http2 on CentOS) service if it's running.
1. Stop the nlserver (nlserver6 for older builds) service if it's running.

After the upgrade:

1. Remove the shared memory using the **ipcrm** command, if the version is older than the current version.
1. Start the nlserver service if it was running.
1. Start the apache2 service if it was running.

Here are the command lines for Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

An example for Linux is available on this [page](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Patches**

* Fixed a minor regression in the cleanup workflow logs.
* Fixed an issue in the workflow **Loading (SOAP)** activity when parsing WSDL files.
* Fixed an issue which caused an error when upgrading numerous workflows using a **Survey** activity to process efficiently a high number of workflows.
* Fixed an intermittent connectivity issue during the processing of inMail messages from the Enhanced MTA. (NEO-20380)
* Fixed an issue that prevented the hot click percentages from showing properly when images were displayed with a 100% width in the HTML. (NEO-23203)
* Fixed an issue that prevented the delivery’s conditional content from being fully displayed in the hot clicks report. (NEO-18729)
* Fixed an issue that skipped the target approval step when resuming a workflow to send a recurring delivery. (NEO-18166)
* Fixed an issue that prevented the **Restart message preparation** button from resuming the delivery after fixing an error in the workflow. (NEO-13488)
* Fixed an issue that could cause deliveries to fail in mid-sourcing mode during the ramp-up phase where target included recipients with Japanese email formats. (NEO-23846)
* Fixed a timezone conversion issue with the Snowflake Connector (NEO-20105)
* Fixed an issue with external accounts using FTP over SSL. (NEO-20498)
* Fixed an issue which could prevent images from being displayed in Line deliveries. (NEO-23207)
* Fixed an issue that caused an error when publishing an offer. (NEO-23312)
* Fixed an issue with push notifications which allowed test connections to work in mobile applications, even when the certificate had expired. (NEO-22991)
* Fixed an issue which could affect push notifications when sent at a high frequency. (NEO-20516)
* Fixed an issue that caused the tracking data to include duplicates even though the tracking logs did not. (NEO-20040)
* Fixed an issue that caused duplicate transactional emails to be sent after a tracking server communication failure was fixed. (NEO-23640)
* Fixed an issue that deleted the encoding parameter value when redirecting from a tracking URL (impact on Japanese characters). (NEO-25637)
* Fixed an issue that could prevent a query from working when comparing float numbers. (NEO-23243)
* Fixed an issue that could prevent the **Modified by** column content from displaying after restarting a workflow. (NEO-23035)
* Fixed an issue that caused the tracking technical workflow to fail when downloading logs from a second container. (NEO-23159)
* Fixed an issue that could cause workflows to fail when running an **Enrichment** activity. (NEO-17338)
* A check has been added to the **Doubles to keep** field in the **Deduplication** workflow activity to prevent entering null or negative values.
* Removed the **Scheduler wizard** from the recurring campaigns to avoid mentioning hours and minutes. Only dates are taken into account.
* Fixed an issue with additional storage fields when creating deliveries through the **Computed by a script** option in the **Script** workflow activity. (NEO-20609)
* Fixed an issue that prevented ghost workflows from being deleted within the database cleanup tasks.
* Fixed an issue which caused the **Billing (active profiles)** technical workflow to fail. (NEO-19777)
* Fixed a regression issue when using the ACS Connector feature which prevented the connection to a Campaign Standard instance (incorrect management of the FOH/FOH2 connection). (NEO-23433)
* Fixed an issue which prevented you from to creating a schema extension on a primary key with multiple columns with a Hadoop table. (NEO-17390)
* Fixed an issue in the **Loading (SOAP)** activity that could prevent WSDL files from being loaded from a URL. (NEO-16924)
* Fixed an issue which prevented you from performing an **Unconditional stop** through the console when multiple active workflow servers were load balanced. (NEO-19556)
* Fixed a regression causing the cleanup workflow to crash.
* Fixed an issue that could occur when publishing a template on an execution instance.
* Fixed an issue that could prevent the collectPrivacyRequests technical workflow from running. (NEO-20513, NEO-25169)
* Fixed issues that could happen when trying to connect to Audience Manager after upgrading to build 9080. (NEO-20511, NEO-25167)
* Fixed issues that could occur when exporting reports in PDF or XLS format. (NEO-20982, NEO-23493, NEO-23348)
* Fixed an issue that could display a delivery twice in the delivery list after it was sent.
* Fixed an issue with delivery preparation that could occur when the routing configuration was set to send the delivery via mid-sourcing.
* Fixed an issue that could display an error message when clicking a web application link within a Line message.
* Fixed an issue that deleted the **Incremental query** activity history after running the cleanup workflow.
* Fixed an issue when creating a mid-sourcing external account where the NmsMidSourcing_LastBroadLog_&lt;InternalName&gt; option was missing.
* Fixed a regression issue on database connection causing the web server to constantly restart due to a database encoding problem. This could lead to overconsumption. (NEO-23264)


## Release 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Release 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_April 15, 2021_

* Fixed a client console regression which caused persistent error messages on the IMS connection screen. (NEO-34821)

**Console upgrade only is mandatory. No server upgrade is required.**

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_March 22, 2021_

* Fixed a regression preventing the usage of some components of the console, such as the date picker and images management in deliveries. (NEO-31453, NEO-31454)

**Console upgrade only is mandatory. No server upgrade is required.** 

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_December 23, 2020_

>[!CAUTION]
>
> * This release comes with a new connection protocol: if you are connecting to Campaign through Adobe Identity Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**. [Learn more](../../technotes/using/ims-updates.md)
>
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 

* The connection protocol has been updated to follow the new IMS authentication mechanism. 
* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Release 20.1.3 - Build 9124{#release-20-1-3-build-9124}

_May 6, 2020_

* Fixed an issue with the **File Transfer** activity which prevented SFTP key based authentication from working on Debian 9. (NEO-23183) 

### ![](assets/do-not-localize/red_2.png) Release 20.1.2 - Build 9123{#release-20-1-2-build-9123}

_March 13, 2020_

* Fixed an issue that prevented version deployment on Red Hat 7 servers. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Release 20.1 - Build 9122{#release-20-1-build-9122}

_February 17, 2020_

**What's new?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake is a fully managed cloud data warehouse built to scale on both storage and compute level. With this new connector, Adobe Campaign can now leverage the power of Snowflake to perform Big Data Segmentation. This connector is available to all customers, including hosted by Adobe.</p>
    <p>For more information, refer to the <a href="../../installation/using/configure-fda-snowflake.md">detailed documentation</a> and <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">tutorial video</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop FDA Connector Enhancements</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>The Hadoop FDA Connector has been improved to support Hadoop 3.0 as well as Cloudera.</p>
    <p>For more information, refer to the <a href="../../installation/using/configure-fda-hadoop.md">detailed documentation</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* Improved security in report configuration to protect from clickjacking. This applies to new reports. For old reports, you need to republish them to apply changes. (NEO-13282)

* Fix a small memory issue in cryptString. (NEO-20071)

* Improved monitor JSP to fix an internal IP disclosure. (NEO-16821)

* Fixed an issue where stack trace information could be displayed to non admin users. (NEO-12388)

* Improved the management of cached data from previous sessions. (NEO-17039)

* Fixed an issue that prevented the logins.log file from recording successful login attempts through IMS. (NEO-11004)

**Improvements**

* iOS 13 is now supported with the HTTP2 connector.

* Improved quarantine management and cleanup of the tables used by the push notification feature (nms:address and nms:appSubscriptionRcp). For iOS (HTTP2 connector only), disabled tokens are now handled in the same way as for Android. The disable flag is now set in the NmsAppSubscriptionRcp table. [Read more](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* A new option has been added in the **JavaScript code** and **Advanced JavaScript code** workflow activities to define a time-out period. This prevents the JavaScript execution phase from running for too long. If the time-out period elapses, the workflow is stopped. The default time-out is 1 hour. [Read more](../../workflow/using/sql-code-and-javascript-code.md)

* The delivery analysis is now stopped when no matching affinity is found on the mid-sourcing server, with the corresponding error message being displayed.

* Database failover for Postgres is now supported: when the database server crashes and restarts, Campaign now reconnects to it automatically.

* The **Start Pending** view has been added to the Administration > Audit > Workflows Status node. This allows you to monitor all workflows on your instance that are waiting to be started by the **operationMgt** process. This view comes with the Marketing campaigns package. [Read more](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Other changes**

* On Linux, the nlserver service startup now uses a systemd unit instead of the /etc/init.d/nlserver6 script. The migration to the new startup scheme is performed automatically when you install the 20.1 package. The /etc/init.d/nlserver6 is still provided but for interacting with the nlserver service (start, restart, stop, etc.), we recommend that you use the systemctl command directly.

* The most consuming custom tables have been moved from the **xtkNewId** sequence to dedicated sequences. [Read more](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) 

* Improved query performance which could be affected by unnecessary database connections.

* Improved the performance of the database update wizard to make fewer SQL statements in order to optimize response time.

* The database record management was enhanced.

* The robustness of the connection pool has been improved, which may prevent unexpected connection failures from happening too often.

* The email address validation rules to send an address to quarantine in case of a soft error have been enhanced. [Read more](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* For Debian, Campaign now uses system PCRE libraries when they are available.

* Campaign now allows the use of a more recent system ODBC library.

* A timeout has been added to the LINE servlet when opening a connection to load a rich image. If the image is taking too much time to load, the servlet stops the connection to avoid a bottleneck.

**Patches**

* Fixed an account key encryption issue when using the Hadoop connector. 

* Fixed a regression issue due to the implementation of SSL certification which caused the user connection to fail on Windows server. (NEO-20629)

* Fixed an issue with the incremental query activity in case of negative workflow IDs. (NEO-19779)

* Fixed an encoding issue when running queries via the Netezza FDA connector. (NEO-19594)

* Fixed an issue which led to an error when using the POST method in the **Web Download** workflow event activity.

* Fixed an issue with offer proposition generation. (NEO-18176)

* Fixed a footer display issue when using the acquisition web form template.

* Fixed an issue when parsing the URLs in the content of continuous deliveries which could cause them to crash. (NEO-16910)

* Fixed an issue with the **Start** and **End** fields not being computed when creating a new campaign.

* Fixed an issue with the **File Download** workflow activity when using a URL.

* Fixed an issue when previewing an imported list in a query activity of a report. (NEO-13119)

* Fixed an issue which displayed an outdated image when selecting the **Powered by Campaign** personalization block in the email editor. 

* The network communication between the client and the server has been improved.

* Fixed an issue when too many workflows are created in the same campaign. Now, you cannot create more than 28 workflows. A warning is displayed.

* Fixed an issue when using the **A selection of columns** reconciliation option in a **Union** workflow activity.

* Fixed a console crash issue that could occur when using a corrupted enrichment list in a workflow. (NEO-18096)

* Fixed various console crash issues that could occur in workflows (NEO-18010, NEO-18032)

* Fixed an issue which allowed the execution of an **External signal** workflow activity even when it was disabled. (NEO-17524)

* Fixed an issue when creating a new schema.

* Fixed a tracking issue when sending SMS messages. (NEO-19595)

* Fixed an issue that displayed incorrect targeted audience number in delivery indicators. 

* Fixed an issue that displayed incorrect percentages when generating a descriptive report via a workflow activity. (NEO-14314)

* Fixed an issue that made the delivery throughput report show different numbers when time view parameter. (NEO-11783)

* Fixed an issue that prevented the transactional messages tracking indicators from being updated by the Tracking workflow. (NEO-17770)

* Fixed a regression issue that caused the web process to crash and restart when requesting an offer through SOAP. (NEO-19482)

* Fixed an issue that prevented from uploading data to public resources if the upload directory was a remote shared location. (NEO-19361)

* Fixed an issue that caused the **Import audiences from the Adobe Experience Cloud** technical workflow tp constantly fail. (NEO-18463)

* Fixed an issue that prevented deliveries from being sent when using templates imported from Experience Manager. (NEO-17540)

* Fixed an issue that occurred after upgrading to build 9032 and preventing the instance from connecting to the FTP server over SSL protocol. (NEO-20498)

* Fixed an issue that occurred when deleting, inserting or updating a large amount of data with the **Update data** activity in a workflow using an FDA schema as the targeting dimension. (NEO-13280)

* Fixed an issue preventing emails from being sent when there was Javascript code outside of the HTML content tag. (NEO-18628)

* Fixed an issue that occurred when trying to display the mirror page from the delivery logs of a sent message. (NEO-17976)

* Fixed an issue that prevented the **Link to mirror page** personalization block from being displayed in the **Text content** tab after clicking **Import HTML** in a delivery. (NEO-17568)

* The error message displayed when clicking a link to a mirror page that expired has been clarified. (NEO-17340)

* Fixed an issue that prevented some buttons from being used in the **Data distribution** creation screen.

* Fixed an issue that occurred when scheduling a delivery activity in an instance with Asia/Kolkata as the time zone. (NEO-20001)

* An error is now displayed when a delivery has an affinity configuration issue. 

* Fixed an issue which displayed an incorrect version tag number in the **About** menu.

* Fixed an issue that occurred when trying to update the routing account from a recurring delivery's properties in a workflow. (NEO-18684)

* Fixed an issue that occurred when connecting to the instance through the redirection module, which prevented the connection from being cleaned properly once closed.
