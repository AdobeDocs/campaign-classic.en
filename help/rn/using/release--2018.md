---
product: campaign
title: Campaign Classic 2018 releases
description: Learn more about Campaign Classic 2018 releases
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: yes
hide: yes
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
---
# 2018 releases{#release-2018}



## Release 18.10

### Release 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 July 2019

**Improvements**

* We now allow the deletion of dummy records created in Microsoft Dynamics during import workflow.
* Fixed an issue with the File Collector workflow activity which could log errors in loop when the access to a file was denied. (NEO-12085)
* Fixed an issue which caused reporting discrepancies between user activities and tracking reports for the open delivery indicator. (NEO-11742)
* Improved permissions to execute the security zone package when using internal account.
* Fixed an issue which could cause errors in the mtachild logs. (NEO-8978)

### Release 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 April 2019

**Improvements**

* Fixed an issue with SQL deadlock which caused delivery analysis to fail in case of simultaneous analysis/sending (when two deliveries were analyzed at the same time). (NEO-13026)
* Removed the 10,000 record limit in Workflow Heatmap to fix a missing data issue. (NEO-12329)
* Fixed an issue when using the "Keep all additional data from the main set" option in an enrichment workflow activity. (NEO-13291)

### Release 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 April 2019

**Improvements**

* Fixed an issue with the computing process of tracking indicators for transactional messages. (NEO-12529, NEO-12581)
* Fixed an issue with the HTTPRequest API which did not wait for all callbacks to finish. (NEO-12628)
* Indexes were added in the coupon temporary tables to optimize delivery sending. (NEO-12437)
* Fixed an issue when analyzing a message which targeted recipients for Japanese (.JP) domains. (NEO-12246)
* In the Analytics integration, the retrieval of AAM segment data with % character is now allowed. (NEO-12025)
* Fixed a Tomcat crash issue when sending push notifications using HTTP2. (NEO-12701)

### Release 18.10.3 - Build 8981{#release-18-10-3-build-8981}

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

### Release 18.10.2 - Build 8978{#release-18-10-2-build-8978}

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
* Fixed an Oracle error in Workflow Heatmap.
* Fixed a right issue when adding an offer proposition in an enrichment activity.
* Fixed an SQL data management connection issue.
* Fixed an issue with the generation of temporary workflow table names in case of negative IDs.
* Fixed an issue with the calculation of workflow durations in Workflow HeatMap.


### Release 18.10.1 - Build 8977{#release-18-10-build-8977}

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
    </ul> <p>As a part of GCM depreciation by Google, Android V2 connector now allows connections only to the FCM server.</p><p>For more information, refer to the <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">detailed documentation</a>.</p> </td> 
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

* Campaign Classic APIs are now available in a [dedicated page](https://experienceleague.adobe.com/developer/campaign-api/api/index.html). If you were using the jsapi.chm file, you should now refer to the new online version.
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

## Release 18.6

### Release 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 August 2018

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
   <td> Query banding<br /> </td> 
   <td> <p>When multiple Campaign users connect to the same FDA Teradata external account, you can now pass a query band (key/value pairs) specific to each user. Each time a Campaign user performs a query on the Teradata database, Adobe Campaign is now able to send meta data associated to the user. These data, which consist in a list of keys and values can then be used by Teradata administrators for audit purposes or to manage access rights, for example.</p><p>For more information, refer to the <a href="../../installation/using/external-accounts.md">detailed documentation</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Improvements**

* Email archiving logs have been enhanced, which makes it easier and clearer to check which emails have been successfully delivered or have failed through BCC archiving. (NEO-10675)
* Fixed an issue which led to the display of load balancer IPs instead of customer IPs in the tracking broadlogs. (NEO-11295)
* Fixed a random issue causing the properties of a delivery to be wrongly overwritten. (NEO-11015)
* Fixed a syntax error when sorting enrichment activity results. (NEO-11394)
* Fixed an issue when using calculated fields in a **[!UICONTROL Survey answers]** workflow activity. (NEO-11382)
* Tomcat has been updated to prevent vulnerabilities exploitation. (NEO-11503)
* Fixed an error with LATIN1 encoding when using an FDA Connection to a PostgreSQL database. (NEO-11299)
* Fixed an issue that occurred when using the **[!UICONTROL Prepare the personalization data with a workflow]** delivery option. (NEO-11047)
* Fixed a postupgrade issue which prevented sending SMS from being sent when using an extended connector.
* Improved package import/export (log and region were added in the interface).
* Fixed an issue which displayed useless errors in the postupgrade log when a **[!UICONTROL Survey answers]** workflow activity was not fully configured.

**Technical evolutions**

Query banding

A specific key (PROXYUSER or PROXYROLE) is used to associate a Teradata user or role to a Campaign user. A new permission has been added to use this proxy user/role. You need to add the GRANT CONNECT THROUGH access right to the database account (the one defined in the Teradata external account).

A new tab has been added in the Teradata external accounts. The **[!UICONTROL Query banding]** tab includes the following options:

* **[!UICONTROL Active]**: check this box to activate the feature.
* **[!UICONTROL Default]**: enter a default query banding that will be used if a user has no associated query banding. If there is no default query banding defined, the users who have no associated query banding will not be able to use Teradata.
* **[!UICONTROL Users]**: for each user, specify a query banding. You can add as many key/value pairs as you need. For example: ‘priority=1;workload=high;’

For more information on query banding, refer to these articles:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw) 
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Release 18.6.1 - Build 8947{#release-18-6-build-8947}

25 June 2018

>[!CAUTION]
>
>This build has been recalled. Please [upgrade to the latest build](../../production/using/build-upgrade.md) or contact [technical support](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Security improvements<br /> </td> 
   <td> A series of security improvements has been added to Campaign Classic. Improvements and fixes are listed below.<br /> </td> 
  </tr> 
  <tr> 
   <td> Support of Windows Server 2016<br /> </td> 
   <td> Adobe Campaign is now compatible with Windows Server 2016. Refer to <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic Compatibility matrix</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

decryptString

The **decryptString** function is deprecated. Refer to the [Deprecated and Removed Features](deprecated-features.md) article.

For new customers, this function is now only used to decrypt the recipient's crypted ID in landing pages. To decrypt passwords stored in an external account, use the new **decryptPassword** function.

For existing customers, the behavior of this function is not changed but we recommend that you use **decryptPassword** instead of **decryptString**. The **XtkSecurity_Unsafe_DecryptString** compatibility option is added by the postupgrade and activated by default, allowing you to keep using the function. If you want to deactivate **decryptString**, deactivate the option.

decryptPassword

The **decryptPassword** function has been added. It allows you to decrypt a password stored in an external account. Refer to the [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) documentation for more information.

File APIs

For new installations, folder access via file APIs is limited to the **var**, **sftp** and temporary folders of Adobe Campaign.

For existing customers, file APIs can no longer access the **conf** folder of Adobe Campaign. The **XtkSecurity_Disable_JSFileSandboxing** compatibility option is added by the postupgrade and activated by default, allowing you to keep accessing the other folders. If you want to limit the access to the **var**, **sftp** and temporary folders of Adobe Campaign, deactivate the option.

**Patch**

* Fixed an issue that could affect SMS transactional message performance. (NEO-9812)

## Release 18.4

### Release 18.4.5 - Build 8937{#release-18-4-5-build-8937}

21 November 2018

**Improvements**

* Fixed various issues when running workflows using MySQL on FDA. (NEO-11652)
* Fixed an issue which caused a portion of the delivery population to remain in pending state, in specific cases. (NEO-11336) 
* Fixed an intermittent issue with the SMS auto response. (NEO-11811) 
* Fixed an ID exhaustion issue when using seed addresses in a delivery. (NEO-11842)
* Fixed a syntax error when performing a sort in an enrichment workflow activity. (NEO-11394) 
* Fixed an issue which could cause a web server crash when restarting IIS. (NEO-10862) 
* Fixed an issue which could cause the tracking workflow to fail after a build upgrade (FDA - SQL). (NEO-11635) 
* Fixed an issue which could cause workflow list data to be lost. (NEO-11696) 
* Fixed a performance issue when sending push notifications. (NEO-11787)
* Fixed an issue which prevented web tracking from working for "com.au" domains (NEO-4385). 
* Fixed a client freeze issue which could occur when using complex workflows. (NEO-11847)
* Fixed an Oracle error when saving a new delivery after selecting an element of a specific schema (NEO-11682). 
* Fixed an issue when querying a field containing characters with accents (FDA/Teradata). The external account now allows you to change the encoding used to communicate with the Teradata driver. (NEO-11818). 
* Fixed a tracking issue when passing URLs in additional variables in a push notification which could lead to mis-formatted or incorrect data received by the mobile application. (NEO-11468, NEO-11960) 
* Fixed an issue which caused a display issue when using a distribution of values with a 1:N link. (NEO-11820)
* Fixed an issue which prevented bulk load from working on Teradata 16. 
* Increased the buffer size for timestamp on Teradata to avoid binding issues with 15.10 driver. 
* Improved the management of long name indexes which could cause postupgrade issues. 
* Improved shared memory available time during children dead processing (MTA).
* Fixed a potential deadlock in Apache (tracking).


### Release 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1 August 2018

**Improvements**

* Email archiving logs have been enhanced, which makes it easier and clearer to check which emails have been successfully delivered or have failed through BCC archiving. (NEO-10675)
* Fixed an issue which led to the display of load balancer IPs instead of customer IPs in the tracking broadlogs. (NEO-11295)
* Fixed an error with LATIN1 encoding when using an FDA Connection to a PostgreSQL database. (NEO-11299)
* Fixed an issue that occurred when using the **[!UICONTROL Prepare the personalization data with a workflow]** delivery option. (NEO-11047, NEO-11301)
* Fixed a random issue causing the properties of a delivery to be wrongly overwritten. (NEO-11015)
* Fixed an issue when using calculated fields in a **[!UICONTROL Survey answers]** workflow activity. (NEO-11382)
* Fixed an issue when using data stored in XML in a **[!UICONTROL Survey answers]** workflow activity. (NEO-10816)
* Fixed an issue when performing the server upgrade with build 8935.
* Fixed an issue which displayed useless errors in the postupgrade log when a **[!UICONTROL Survey answers]** workflow activity was not fully configured.
* FDA Teradata: fixed an issue with auto-incremented fields and indexes in SQL tables.

### Release 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 June 2018

**Improvements**

* Fixed a tracking encoding issue with Microsoft Edge and Internet Explorer. (NEO-11257)
* Fixed an issue with image link personalization in LINE deliveries. (NEO-11077)
* Fixed an issue that prevented the ID sequence generation mechanism from working correctly. (NEO-11115)
* Fixed an issue which prevented privacy (GDPR) requests from working when using a custom namespace with an integer type reconciliation key. (NEO-11123)
* Fixed an error which could occur when using the **[!UICONTROL Distribution of values]** option in **[!UICONTROL Query]** workflow activities. (NEO-10958)
* Fixed an issue when syncing offer spaces from the marketing instance to the interaction instance. (NEO-11162)
* Improved the management of long name indexes during postupgrade

### Release 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 May 2018

**Improvements**

* Fixed an issue which prevented the Windows Server update from working correctly.
* Fixed an issue in the **[!UICONTROL Survey Result]** activity when using data stored in XML. The report was displayed incorrectly. (NEO-10816)
* Fixed a performance issue which could occur with the inMail process when using a bounce mail server. (NEO-10641)
* Fixed a database upgrade issue which could occur when upgrading more than 1000 schemas.

### Release 18.4.1 - Build 8931{#release-18-4-build-8931}

24 Apr 2018

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
   <td> EU General Data Protection Regulation (GDPR)<br /> </td> 
   <td> <p>GDPR is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.</p> <p>In addition to the privacy capabilities already available in Adobe Campaign (including consent management, data retention settings, and user roles), we are taking this opportunity in our role as Data Processor to include additional capabilities, to help facilitate your readiness as Data Controller for certain GDPR requests:</p> 
    <ul> 
     <li> <p>Right to Access: allows the Data Subject to receive a copy of their personal data captured by Data Controllers, potentially including data stored in Adobe Campaign.</p> </li> 
     <li> <p>Right to Delete: entitles the Data Subject to have their personal data captured by Data Controllers erased, potentially including data stored in Adobe Campaign.</p> </li> 
    </ul> For more information, refer to the <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">detailed documentation</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Active profiles<br /> </td> 
   <td> <p>Adobe Campaign now provides the list of active profiles, updated monthly through a dedicated workflow.</p> <p>For more information, refer to the <a href="../../platform/using/about-profiles.md#active-profiles">detailed documentation</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Android Push Connector enhancement<br /> </td> 
   <td> <p>The Android connector has been enhanced to support higher throughput. </p> <p>For more information, refer to the <a href="../../delivery/using/configuring-the-mobile-application.md">detailed documentation</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* Expansion of external entities is now disabled to prevent potential attacks from unauthenticated users. (NEO-10173)
* Hardened permissions to prevent standard users from changing the instance configuration parameters such as application access URLs, LDAP settings, etc. (NEO-10171)
* Fixed an issue which could reveal sensitive information via stack traces. Error details are now logged in the back end to a location unaccessible from the external network. (NEO-10176)
* Hardened permissions to prevent standard users from viewing an administrator's uploaded documents and/or exported packages. (NEO-10170)

**Improvements**

* **LINE channel - architecture enhancement**: As with all other channels in Adobe Campaign, the LINE channel is now supported across all deployment types: hosted, hybrid, and on-premise. 
* **Sequence auto-generation**: The ID generation mechanism has been enhanced to increase the lifespan of Campaign instances with large volumes of objects.

**Other changes**

* A new mode is available for package import using command line, allowing circular dependencies (not recommended for large packages). See the 'Technical evolutions' section for more information. (NEO-8979) 
* Improved performance for large amount of data loading in Teradata and fixed an issue which prevented from displaying the right value of data processed in the log. (NEO-10429)
* Importing audiences from Audience Manager now works with split files. Previously, only the last file of the segment was imported by the importSharedAudience technical workflow. (NEO-10156)
* On Windows, the Campaign server default installation path has changed. When launching the 64-bit version setup, the default installation path is now: **C:\Program Files\Adobe\Adobe Campaign Classic v7** instead of **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* The default MX rules have been enhanced to include more domains and optimize throughput.
* Enforced access restrictions on the deployment wizard SOAP call (xtk:serverOptions#SaveOptions).
* The weka.jar obsolete library has been removed and the OpenSSL library has been updated for security optimization.
* Improved the billing technical workflow to secure instances performances.
* The ability for administrators to set or reset the password of any operator has been restored. To do this, right-click on an operator, select **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** and set the operator's new password. We recommend that operators change their password when they first reconnect. For more information, refer to the [detailed documentation](../../production/using/lost-password.md).
* To support the new multitenancy feature in Adobe Target, a new “at_property” parameter can now be added to URLs when configuring options and external accounts for the integration with Target. The value to use for this parameter can be found in Adobe Target and will be used by Campaign when performing calls to Target. For more information, refer to the [detailed documentation](../../integrations/using/inserting-a-dynamic-image.md).
* You can now specify a default landing page to open when clicking on an image served by Adobe Target. Previously, clicking that image was leading to the default image set when creating the email instead. For more information, refer to the [detailed documentation](../../integrations/using/inserting-a-dynamic-image.md).
* Added **Enable SMPP traces** checkbox in the external account to force traces output. For more information, refer to the [detailed documentation](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Technical evolutions**

queryDef

queryDef has been modified regarding the "orderBy" clause. Before the change, the primary key of the queried table would implicitly be added to the "orderBy" clauses. On some database engines (postgresql at least), it prevents the use of indexes (all fields of the orderBy clause must be covered by the same index). If you were dependent of this behavior, you will have to explicitly add the primary key in your "orderBy" clause.

For example, if you have the following query:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

It would implicitly be handed as (before the 18.4 changes):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode function

The 'urlEncode' JavaScript function was not working properly for non ASCII characters. It has been corrected and it should now work with all Unicode characters (including Japanese characters). If you were relying on the 'urlEncode' behavior for non ASCII character, you will have to adapt your code.

Package import new mode

A new mode is available for package import using command line, allowing circular dependencies (not recommended for large packages). The existing functionality is kept. For such packages with circular dependencies, a new flag **-usejs** has been added to the command line package import. When executed, it will use the JSEngine like when the package import is performed from the interface.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patches**

* Fixed a synchronization issue when replicating delivery and tracking logs from Adobe Campaign Standard to Adobe Campaign Classic. (NEO-10023)
* Fixed an issue with the handling of Error and Log tables in Teradata when an ETL workflow was resuming after a failure on a fast load operation. The Error and Log tables are now deleted properly each time the workflow resumes. (NEO-10672)
* Fixed a postupgrade issue to automatically install the Hive package (needed for Hadoop) if the FDA package is installed. (NEO-10592)
* Fixed an error that treated invalid domains as a **Not defined** error. (NEO-10248)
* Fixed an issue which duplicated logs in the deliveryLogStats table when sending android push deliveries. (NEO-10234)
* Fixed an issue which could lead to certain bar code formats not being readable by bar code scanners. (NEO-10125)
* Fixed an issue with the 'urlEncode' JavaScript function when using non ASCII characters. See the 'Technical evolutions' section for more information. (NEO-10123)
* Fixed an issue when executing a query including sha256 functions on Teradata databases. (NEO-10119)
* Fixed workflow memory errors that could occur in the SalesForce activity when using very large SalesForce tables. (NEO-9900) 
* Fixed an issue with the **Generate complement** option in targeting workflow activities when using FDA. (NEO-9878) 
* Fixed an issue which could lead to the **Processed** and **Success** metrics not being updated on the marketing instance when using mid-sourcing. (NEO-9454) 
* Fixed Interaction non-reproposition rules when more than 10k offers in total in the platform (NEO-9352) 
* Fixed an issue that could prevent from specifying the target of a delivery when using an XML external file. (NEO-9312) 
* Fixed an issue that could lead to workflow errors when running a hypothesis on an offer and updating the status of the proposition. (NEO-9304) 
* Fixed errors occurring during delivery analysis when using pressure rules based on an attribute of the Android delivery mapping. (NEO-9202) 
* Fixed an issue when sorting on columns in recipient list that could result in performance issues. For more information on the queryDef modifications, see the 'Technical evolutions' section below. (NEO-9042)
* Fixed an issue where the links in an approval email could point to an incorrect login URL, especially when using a Federated ID login type. (NEO-9011) 
* Fixed an issue which could lead to wrong dates being displayed in the date pickers of reports for certain timezones. (NEO-9007) 
* Fixed an issue which prevented from viewing the target of an outbound when using an FDA SQL database. (NEO-8924) 
* Fixed an issue that led the MS Dynamics CRM connector to fail to pull data for the first 7 days of month. (NEO-8803) 
* Fixed an error with Analytics integration that prevented users to include international characters. (NEO-8719) 
* Fixed an issue that could enable workflow editing without the proper rights. (NEO-8708) 
* Fixed an issue with FDA over HTTPs when using Message Center in a hybrid architecture, leading to connection drop or loss of connection (timeout). (NEO-8438) 
* Fixed workflow errors occurring in incremental query activity for negative IDs. (NEO-8229) 
* Fixed an issue that could lead to the display of double scroll bars in certain screens. (NEO-8208) 
* Fixed an issue that led to an error message being displayed when running the update database structure wizard. The PostUpgrade will execute a rename of indexes with names longer than 30. Be aware that for large tables, the index replacement will take time. (NEO-7983) 
* Fixed an issue with tracking logs not getting synched correctly from Message Center execution instance to control instance. (NEO-7286) 
* Fixed a performance issue with the offer enrichment activity. (NEO-7263) 
* Fixed an issue preventing from using the DaysAgo function when querying a Redshift database via FDA. (NEO-7099)
* Fixed a regression in data management that prevented index creation on Enrichment-like workflow activities.
* Fixed an issue which could occur when creating external resources with the title @id
* Fixed an issue which could occur when uploading zipped files via a FTP server or when uploading files with wildcards in the file name.
* Fixed an issue with long base type enumerations in external custom resources created into Campaign Standard.
* Fixed an issue that could lead to SMS being sent even when the connection with the provider failed resulting in SMS losses.
* Fixed an error that let an SMTP connection get stuck indefinitely. 
* Fixed an issue with pressure typology rules during message preparation when using a LINE mapping or when filtering and targeting schemas differ.
