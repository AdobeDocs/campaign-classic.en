---
solution: Campaign Classic
product: campaign
title: Release 20.1
description: Release 20.1
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: 7e4234c9-3d8f-4014-a870-75e91cfad725
---
# Release 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) Release 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_March 22, 2021_

* Fixed a regression preventing the usage of some components of the console, such as the date picker and images management in deliveries. (NEO-31453, NEO-31454)

**Console upgrade only is mandatory. No server upgrade is required.** 

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_December 23, 2020_

>[!CAUTION]
>
> * This release comes with a new connection protocol: if you are connecting to Campaign through Adobe Identity Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**.
>
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 

* The connection protocol has been updated to follow the new IMS authentication mechanism. 
* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Release 20.1.3 - Build 9124{#release-20-1-3-build-9124}

_May 6, 2020_

* Fixed an issue with the **File Transfer** activity which prevented SFTP key based authentication from working on Debian 9. (NEO-23183) 

## ![](assets/do-not-localize/red_2.png) Release 20.1.2 - Build 9123{#release-20-1-2-build-9123}

_March 13, 2020_

* Fixed an issue that prevented version deployment on Red Hat 7 servers. (NEO-23332)

## ![](assets/do-not-localize/red_2.png) Release 20.1 - Build 9122{#release-20-1-build-9122}

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
    <p>For more information, refer to the <a href="../../installation/using/configure-fda-snowflake.md">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">tutorial video</a>.</p>
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

* A new option has been added in the **JavaScript code** and **Advanced JavaScript code** workflow activities to define a time-out period. This prevents the javascript execution phase from running for too long. If the time-out period elapses, the workflow is stopped. The default time-out is 1 hour. [Read more](../../workflow/using/sql-code-and-javascript-code.md)

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
