---
product: campaign
title: Campaign 18.4 release notes
description: Release notes for Campaign 18.4
feature: 
role:
level:
exl-id: bbad81ba-a09f-4d67-9309-628ea7a08c9b
---
# Release 18.4{#release-18-4}

## Release 18.4.5 - Build 8937{#release-18-4-5-build-8937}

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

## Release 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1 August 2018

**Improvements**

* Email archiving logs have been enhanced, which makes it easier and clearer to check which emails have been successfully delivered or have failed through BCC archiving. (NEO-10675)
* Fixed an issue which led to the display of load balancer IPs instead of customer IPs in the tracking broadlogs. (NEO-11295)
* Fixed an error with LATIN1 encoding when using an FDA Connection to a PostgreSQL database. (NEO-11299)
* Fixed an issue that occured when using the **[!UICONTROL Prepare the personalization data with a workflow]** delivery option. (NEO-11047, NEO-11301)
* Fixed a random issue causing the properties of a delivery to be wrongly overwritten. (NEO-11015)
* Fixed an issue when using calculated fields in a **[!UICONTROL Survey answers]** workflow activity. (NEO-11382)
* Fixed an issue when using data stored in XML in a **[!UICONTROL Survey answers]** workflow activity. (NEO-10816)
* Fixed an issue when performing the server upgrade with build 8935.
* Fixed an issue which displayed useless errors in the postupgrade log when a **[!UICONTROL Survey answers]** workflow activity was not fully configured.
* FDA Teradata: fixed an issue with auto-incremented fields and indexes in SQL tables.

## Release 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 June 2018

**Improvements**

* Fixed a tracking encoding issue with Microsoft Edge and Internet Explorer. (NEO-11257)
* Fixed an issue with image link personalization in LINE deliveries. (NEO-11077)
* Fixed an issue that prevented the ID sequence generation mechanism from working correctly. (NEO-11115)
* Fixed an issue which prevented privacy (GDPR) requests from working when using a custom namespace with an integer type reconciliation key. (NEO-11123)
* Fixed an error which could occur when using the **[!UICONTROL Distribution of values]** option in **[!UICONTROL Query]** workflow activities. (NEO-10958)
* Fixed an issue when syncing offer spaces from the marketing instance to the interaction instance. (NEO-11162)
* Improved the management of long name indexes during postupgrade

## Release 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 May 2018

**Improvements**

* Fixed an issue which prevented the Windows Server update from working correctly.
* Fixed an issue in the **[!UICONTROL Survey Result]** activity when using data stored in XML. The report was displayed incorrectly. (NEO-10816)
* Fixed a performance issue which could occur with the inMail process when using a bounce mail server. (NEO-10641)
* Fixed a database upgrade issue which could occur when upgrading more than 1000 schemas.

## Release 18.4 - Build 8931{#release-18-4-build-8931}

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
   <td> <p>GDPR is the European Union’s (EU) new privacy law that harmonizes and modernizes data protection requirements going into effect on May 25, 2018. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.</p> <p>In addition to the privacy capabilities already available in Adobe Campaign (including consent management, data retention settings, and user roles), we are taking this opportunity in our role as Data Processor to include additional capabilities, to help facilitate your readiness as Data Controller for certain GDPR requests:</p> 
    <ul> 
     <li> <p>Right to Access: allows the Data Subject to receive a copy of his/her personal data captured by Data Controllers, potentially including data stored in Adobe Campaign.</p> </li> 
     <li> <p>Right to Delete: entitles the Data Subject to have his/her personal data captured by Data Controllers erased, potentially including data stored in Adobe Campaign.</p> </li> 
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
* **Sequence auto-generation**: The ID generation mechanism has been enhanced to increase the lifespan of Campaign instances with large volumes of objects. For more information, refer to this [technote](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).

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
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
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
