---
title: Release 18.4 - Build 8931
seo-title: Release 18.4 - Build 8931
description: Release 18.4 - Build 8931
seo-description: 
page-status-flag: never-activated
uuid: 7a3b2ece-9ba6-4afc-897c-ff7490351439
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: rn
discoiquuid: f51e04a9-2bd2-4aa3-a292-cb76955ae92a
index: y
internal: n
snippet: y
---

# Release 18.4 - Build 8931{#release-build}

24 Apr 2018

## What's new? {#what-s-new-}

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
   <td> GDPR is the European Union’s (EU) new privacy law that harmonizes and modernizes data protection requirements going into effect on May 25, 2018. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.<br /> In addition to the privacy capabilities already available in Adobe Campaign (including consent management, data retention settings, and user roles), we are taking this opportunity in our role as Data Processor to include additional capabilities, to help facilitate your readiness as Data Controller for certain GDPR requests:<br /> 
    <ul> 
     <li> <p>Right to Access: allows the Data Subject to receive a copy of his/her personal data captured by Data Controllers, potentially including data stored in Adobe Campaign.</p> </li> 
     <li> <p>Right to Delete: entitles the Data Subject to have his/her personal data captured by Data Controllers erased, potentially including data stored in Adobe Campaign.</p> </li> 
    </ul> For more information, refer to the <a href="../getting_started/EN/ACC_GDPR.md">detailed documentation</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Active profiles<br /> </td> 
   <td> Adobe Campaign now provides the list of active profiles, updated monthly through a dedicated workflow.<br /> For more information, refer to the <a href="../../platform/using/about-profiles.md#active-profiles">detailed documentation</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Android Push Connector enhancement<br /> </td> 
   <td> The Android connector has been enhanced to support higher throughput. <br /> For more information, refer to the <a href="../../delivery/using/setting-up-mobile-app-channel.md#android-connectors">detailed documentation</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Security enhancements {#security-enhancements}

* Expansion of external entities is now disabled to prevent potential attacks from unauthenticated users. (NEO-10173)
* Hardened permissions to prevent standard users from changing the instance configuration parameters such as application access URLs, LDAP settings, etc. (NEO-10171)
* Fixed an issue which could reveal sensitive information via stack traces. Error details are now logged in the back end to a location unaccessible from the external network. (NEO-10176)
* Hardened permissions to prevent standard users from viewing an administrator's uploaded documents and/or exported packages. (NEO-10170)

## Improvements {#improvements}

* **LINE channel - architecture enhancement**: As with all other channels in Adobe Campaign, the LINE channel is now supported across all deployment types: hosted, hybrid, and on-premise. 
* **Sequence auto-generation**: The ID generation mechanism has been enhanced to increase the lifespan of Campaign instances with large volumes of objects. For more information, refer to this [technote](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).

## Other changes {#other-changes}

* A new mode is available for package import using command line, allowing circular dependencies (not recommended for large packages). See the 'Technical evolutions' section for more information. (NEO-8979) 
* Improved performance for large amount of data loading in Teradata and fixed an issue which prevented from displaying the right value of data processed in the log. (NEO-10429)
* Importing audiences from Audience Manager now works with split files. Previously, only the last file of the segment was imported by the importSharedAudience technical workflow. (NEO-10156)
* On Windows, the Campaign server default installation path has changed. When launching the 64-bit version setup, the default installation path is now: **C:Program FilesAdobeAdobe Campaign Classic v7** instead of **C:Program Files (x86)AdobeAdobe Campaign Classic v7**
* The default MX rules have been enhanced to include more domains and optimize throughput.
* Enforced access restrictions on the deployment wizard SOAP call (xtk:serverOptions#SaveOptions).
* The weka.jar obsolete library has been removed and the OpenSSL library has been updated for security optimization.
* Improved the billing technical workflow to secure instances performances.
* The ability for administrators to set or reset the password of any operator has been restored. To do this, right-click on an operator, select **Actions** > **Reset password** and set the operator's new password. We recommend that operators change their password when they first reconnect. For more information, refer to the [detailed documentation](../../production/using/lost-password.md).
* To support the new multitenancy feature in Adobe Target, a new “at_property” parameter can now be added to URLs when configuring options and external accounts for the integration with Target. The value to use for this parameter can be found in Adobe Target and will be used by Campaign when performing calls to Target. For more information, refer to the [detailed documentation](../../integrations/using/inserting-a-dynamic-image.md).
* You can now specify a default landing page to open when clicking on an image served by Adobe Target. Previously, clicking that image was leading to the default image set when creating the email instead. For more information, refer to the [detailed documentation](../../integrations/using/inserting-a-dynamic-image.md).
* Added **Enable SMPP traces** checkbox in the external account to force traces output. For more information, refer to the [detailed documentation](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

## Technical evolutions {#technical-evolutions}

**queryDef**

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

**urlEncode function**

The 'urlEncode' JavaScript function was not working properly for non ASCII characters. It has been corrected and it should now work with all Unicode characters (including Japanese characters). If you were relying on the 'urlEncode' behavior for non ASCII character, you will have to adapt your code.

**Package import new mode**

A new mode is available for package import using command line, allowing circular dependencies (not recommended for large packages). The existing functionality is kept. For such packages with circular dependencies, a new flag **-usejs** has been added to the command line package import. When executed, it will use the JSEngine like when the package import is performed from the interface.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

## Patches {#patches}

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

