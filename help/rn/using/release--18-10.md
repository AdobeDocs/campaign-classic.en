---
solution: Campaign Classic
product: campaign
title: Campaign 18.10 release notes
description: Release notes for Campaign 18.10
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: 57996f77-4ac2-402a-95db-b75d4bea4eeb
---
# Release 18.10{#release-18-10}

## Release 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 July 2019

**Improvements**

* We now allow the deletion of dummy records created in Microsoft Dynamics during import workflow.
* Fixed an issue with the File Collector workflow activity which could log errors in loop when the access to a file was denied. (NEO-12085)
* Fixed an issue which caused reporting discrepancies between user activities and tracking reports for the open delivery indicator. (NEO-11742)
* Improved permissions to execute the security zone package when using internal account.
* Fixed an issue which could cause errors in the mtachild logs. (NEO-8978)

## Release 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 April 2019

**Improvements**

* Fixed an issue with SQL deadlock which caused delivery analysis to fail in case of simultaneous analysis/sending (when two deliveries were analyzed at the same time). (NEO-13026)
* Removed the 10,000 record limit in Workflow Heatmap to fix a missing data issue. (NEO-12329)
* Fixed an issue when using the "Keep all additional data from the main set" option in an enrichment workflow activity. (NEO-13291)

## Release 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 April 2019

**Improvements**

* Fixed an issue with the computing process of tracking indicators for transactionnal messages. (NEO-12529, NEO-12581)
* Fixed an issue with the HTTPRequest API which did not wait for all callbacks to finish. (NEO-12628)
* Indexes were added in the coupon temporary tables to optimize delivery sending. (NEO-12437)
* Fixed an issue when analyzing a message which targeted recipients for Japanese (.JP) domains. (NEO-12246)
* In the Analytics integration, the retrieval of AAM segment data with % character is now allowed. (NEO-12025)
* Fixed a Tomcat crash issue when sending push notifications using HTTP2. (NEO-12701)

## Release 18.10.3 - Build 8981{#release-18-10-3-build-8981}

29 January 2019

>[!CAUTION]
>
>This build has been recalled. Please [upgrade to the latest build](../../production/using/build-upgrade.md)  or contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Improvements**

* Fixed an issue with the s3 File Transfer workflow activity. (NEO-12473) 
* Fixed an issue with the Tracking workflow which could fail. (NEO-12520) 
* Fixed an issue with the IMS login. 
* Fixed an issue with the preview and content approval in Transactional messaging when using a large offer ID. 
* Fixed an issue with the Mid-sourcing (delivery counters) workflow. 
* Fixed an issue with the database structure update which dropped new indexes on NmsRecipient. 
* Fixed a console crash that could occur when using the Defined in an external file option for the main target of a delivery. (NEO-12349) 
* Fixed several InMail crashes. 
* Fixed an issue when using an Update data workflow activity to delete records stored in an FDA Teradata database. 
* Fixed inconsistency issues in secret key management. 
* Fixed an issue with the Enrichment activity when typing a field as: xml=true and calculated=true
* Fixed a character escaping issue when sending push notifications on a mobile application. 
* Fixed an issue which prevented from switching from FDA to SOAP synchronization method in a Mid-Sourcing external account.

## Release 18.10.2 - Build 8978{#release-18-10-2-build-8978}

6 December 2018

>[!CAUTION]
>
>This build has been recalled. Please [upgrade to the latest build](../../production/using/build-upgrade.md) or contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Improvements**

* Fixed various issues when running workflows using MySQL on FDA. (NEO-11652)
* Fixed a performance issue when sending push notifications. (NEO-11787)
* Fixed an ID exhaustion issue when using seed addresses in a delivery. (NEO-11842)
* Fixed a client freeze issue which could occur when using complex workflows. (NEO-11847)
* Fixed a display issue when using a distribution of values with a 1:N link. (NEO-11820)
* Fixed an Oracle error in Worflow Heatmap.
* Fixed a right issue when adding an offer proposition in an enrichment activity.
* Fixed an SQL data management connection issue.
* Fixed an issue with the generation of temporary workflow table names in case of negative IDs.
* Fixed an issue with the calculation of workflow durations in Workflow HeatMap.


## Release 18.10 - Build 8977{#release-18-10-build-8977}

5 Nov 2018

>[!CAUTION]
>
>This build has been recalled. Please [upgrade to the latest build](../../production/using/build-upgrade.md) or contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**What's new?**

<table> 
 <thead> 
  <tr> 
   <th> Functionality<br /> </th> 
   <th> Description<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Push notification improvements<br /> </td> 
   <td> A number of enhancements has been implemented for push notification in Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Track silent notifications in iOS </p> </li> 
     <li> <p>Implement feedback on registration calls in iOS</p> </li> 
     <li> <p>Improve iOS delivery preparation speed</p> </li> 
    </ul> <p>As a part of GCM depreciation by Google, Android V2 connector now allows connections only to the FCM server.</p><p>For more information, refer to the <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">detailed documentation</a>. The manual ugrade to FCM is detailed in this <a href="https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html">article</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL Data Management activity<br /> </td> 
   <td> <p>A new data management workflow activity has been added. The <strong>SQL Data Management</strong> activity lets you write or copy-paste your own SQL scripts to create and populate work tables (FDA only). </p> <p>For more information, refer to the <a href="../../workflow/using/sql-data-management.md">detailed documentation</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Workflow monitoring<br /> </td> 
   <td> <p>With the new Adobe Campaign Workflow HeatMap, the platform administrators have a quick graphical representation of all the concurrent workflows, which allows them to monitor the load on the instance and plan workflows accordingly.</p> <p>For more information, refer to the <a href="../../workflow/using/heatmap.md">detailed documentation</a>.</p> <p>The Workflow HeatMap package is also available on demand for builds prior to 8977 (starting build 8700). For more on requesting and installing it, refer to <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">this page</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* Fixed a security issue that could result in vulnerabilities to Server Side Request Forgery (SSRF) attacks and denial of service (DoS) attacks. (NEO-11453)
* Content (tracking redirection, mirror pages, surveys, etc.) will now be served by Campaign with the X-Robots-Tag: nocache header. This prevents the indexation of this content by Internet search engines. (NEO-11101)
* Fixed an XTK injection issue in subscription API (nms:subscription:Unsubscribe and nms:subscription:Subscribe).
* Fixed an XTK injection issue in the unsubscription web application.
* Removed passwords that were insecurely displayed in some SMS logs.

**Improvements**

* Campaign Classic APIs are now available in a [dedicated page](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html). If you were using the jsapi.chm file, you should now refer to the new online version.
* PostgreSQL 10, Debian 9 and Teradata 16.20 are now supported. Refer to the [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).
* When creating an SFTP connection, you can now use proxy authentication. For more information, refer to the [detailed documentation](../../installation/using/file-res-management.md) (NEO-9868)
* The **Date calculation formula** option is now available in the delivery properties when creating a single delivery using the direct mail delivery template. (NEO-9792)
* The domain name management has been improved for cookie tracking and web applications. See the 'Technical evolutions' section below for more information. 
* The import of Adobe Marketing Cloud shared assets in a delivery or landing page has been improved in terms of security and performance.
* A new checkbox is available in the Mobile channel external account to enable verbose SMPP traces in the log file, which makes this output directly accessible from the Adobe Campaign interface.
* In the broadlogs, there is now a distinction between the maximum number of connections and the maximum number of messages per hour. When the limits are reached, it is then possible to know why the throughput is limited. Previously, the same message (‘quota met’) applied to both cases.
* You can now specify an SQL script to execute when acquiring a connection from the pool. This script can be used to set the default schema. This script will be applied after query banding. (NEO-11256) 
* Campaign SDK no longer stores the User ID to comply with our PII regulations. Data is now stored as a hash.
* When importing a package export XML file, Campaign now supports the presence of BOM in the file, even if the encoding is explicitly declared in it.

**Technical evolutions**

Client and server upgrade

>[!CAUTION]
>
>If you have a server that has been updated to 18.10, you will have to use a 18.10 client in order to access your server. The 18.10 client will be able to connect to an older server version.

Domain name management

The domain name management has been improved for cookie tracking and web applications.

Now, all two-letter second-level domain names are supported by default (for example .aa.com). For more complex domain names (for example three-letter second-level domains such as .com.au), you need to add them in the **cookieDomains** option of the serverConf (under the redirection tag). Here is an example:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Index enhancements

Indexes on NmsRecipient have been reworked. This should improve performance on queries that use this table. If you had done an extension of NmsRecipient, you may want to verify that you don't have indexes that duplicate the new indexes (to minimize space usage on the database server). (NEO-8228)

On PostgreSql when using a UTF-8 collation, it's now possible to create indexes that will optimize "LIKE 'string%'" (or "starts with") operations. If you perform other operations on the same column (order by or join for example), another standard index will be required. On the schema side, this will be done by adding indexOption="searchFromStart" on the index definition (it will create a varchar_pattern_ops index instead of a standard btree index). For example (on NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

New indexes have been added to NmsRtEvent and NmsEventHisto (on the "Scheduled" column), this should improve display time on the corresponding form (NEO-11738).

These index changes may lead to an increase of the time required to perform the post-upgrade.

**Patches**

* Fixed an error that prevented files from the **Web download** workflow activity from being downloaded. (NEO-11105)
* Fixed an error that occasionally left the **Sending of indicators and campaign attributes** workflow in a Failed state (NEO-10820).
* Fixed an issue that deleted the recipient list created after running the List update activity in a workflow. (NEO-11696)
* Fixed an issue that incorrectly displayed the campaigns one month ahead in the Campaign calendar (on a Japanese instance). (NEO-11445)
* Fixed an issue that prevented the Analytics configuration to display in the Web Analytics tab of the delivery Properties. (NEO-11619)
* Fixed an error that displayed when trying to edit and save the nms:delivery input form. (NEO-10973)
* Fixed an External account configuration issue that occurred when running a workflow containing a File transfer activity. (NEO-11012)
* Fixed an issue that returned blank lines when using the zcat function to load files in the Data loading activity. (NEO-11273)
* Fixed an issue that generated duplicated broad logs during the analysis of the delivery. (NEO-11360)
* Fixed an issue that led to delivery failing due to missing foreign link key after executing the Enrichment activity in a workflow. (NEO-11537)
* Fixed an issue that prevented correct uninstalling or repairing of Adobe Campaign when the installation path included specific GB18030 Chinese characters.
* Fixed an issue that linked some tracking logs to the wrong delivery. (NEO-11412)
* Fixed an issue that could cause some parts of the delivery logs remaining with pending status for longer than expected. (NEO-11336)
* Fixed an error that occurred when editing a query to add a coupon to a delivery. (NEO-11037)
* Fixed an issue in reports that made the charts always calculate the sum of the values no matter which aggregated operator was selected. (NEO-10913)
* As the "request.scheme" function is deprecated, it has been removed from the JSAPI documentation. (NEO-10828)
* Fixed an issue that prevented some users with specific time zone configurations to log in to Adobe Campaign. (NEO-10712)
* Fixed an issue that occurred when setting up a Mobile channel external account using the Extended generic SMPP connector: if you specified using different parameters for the receiver, the transmitter would incorrectly use those parameters instead of its own parameters.
* Fixed an issue that caused scheduled deliveries to fail when setting a frequency for the pressure rule, because the deliveries were constantly re-calculated after the first arbitration. (NEO-10016)
* Fixed an issue that caused the IIS webserver to crash during the Application Pool recycle process (in nlsrvmod.dll library). (NEO-10862)
* Fixed an issue which could prevent from searching a recipient in the **Profiles and Target** screen. (NEO-8228)
* Fixed an issue which could lead to a time out error when accessing the Event History folder in the case of a high number of records. (NEO-11738)
* Fixed an issue which could lead to LINE delivery recipients being wrongly returned as "Unreachable". (NEO-10833)
* Fixed an issue when executing a workflow query with an additional column on Oracle. (NEO-11615)
* An enhancement has been made to make sure closed connections are not kept in the connection pool for too long. (NEO-11392) 
* Fixed an issue when using a targeting workflow activity (query, data loading (RDBMS), etc.) connected via FDA to an external Oracle table which contained UTF8 characters (in the table name, field name, etc.) and which contained also a primary key constraint with a system-generated default constraint name. (NEO-10714)
* Fixed an issue which could prevent from deleting the HTML content of a delivery. (NEO-11327)
* Fixed an issue with the preview of XML and CSV files in a direct mail after a campaign is run. (NEO-11290)
* Fixed an issue when sorting data in an enrichment workflow activity. (NEO-11394)
* Fixed an issue when sorting data in a custom report. (NEO-10896)
* Fixed an issue that led to errors when using the useVault setting with Teradata. (NEO-11399)
* Fixed an issue that caused the Adobe Campaign client console to crash when deleting multiple query lines. (NEO-10744)
* Fixed an issue that prevented pressure rules to be applied in some case when delivering direct mail. (NEO-9004)
* Fixed an issue that occurred when using the Data loading activity to import a column with the Data type ‘time’: the time separator would be reset even after being removed. (NEO-10743)
* Fixed an issue that prevented the Deliveries folder to be displayed from the Execution folder list in the Delivery properties when editing a recurring delivery. (NEO-11094)
* Fixed an issue that prevented the View population window to display more than 200 records as the resulting target of a Query activity in a workflow. (NEO-11195)
* Fixed an issue in Oracle that prevented a DELETE query to be executed with more than 1000 elements selected. (NEO-11171) 
* Fixed an issue that led to encode URLs as tracked URLs in the additional parameters of an Android push notification delivery. (NEO-11468) 
* Fixed a script error that occurred in the User activities report when setting the parameters to ‘One day intervals’ and ‘Opens’. (NEO-11655)
* Fixed an issue that occurred when connecting to the mid-sourcing server or to Message Center through an authenticated web proxy. (NEO-11309)
* Fixed an Oracle error that occurred when a new delivery composition was saved after selecting an element of a specific schema **based on a SQL view**. (NEO-11682) 
* Fixed an issue which led to generated reject files containing false positives when processing a zip file containing a .csv via a load file activity using the Decompression option.
* xtkjoblog is now purged by the cleanup.
