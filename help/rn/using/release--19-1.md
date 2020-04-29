---
title: Release 19.1
seo-title: Release 19.1
description: Release 19.1
seo-description: 
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
---

# Release 19.1{#release-19-1}

[Build upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) &#124; [Control Panel releases](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) &#124; [Documentation updates](../../rn/using/documentation-updates.md) &#124; [Previous releases](../../rn/using/release--19-1.md) &#124; [Deprecated features](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>General Availability</strong></td>
   <td><img src="assets/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/orange3.png"/><strong>No longer available</strong></td> 
   <td><img src="assets/red3.png"/><strong>Deprecated</strong></td> 
  </tr> 
   <tr> 
   <td>Latest stable build available. Build validated in production.<br>&nbsp;</td>
   <td>Build validated by Adobe. Waiting for production proofing.<br>&nbsp;</td>
   <td>Newer build available with bug fixes. Update is required.<br>&nbsp;</td>
   <td>Contains known regressions. Update is mandatory.<br>&nbsp;</td>
  </tr> 
 </tbody> 
</table>

The **last stable build** is 9032 (3a9dc9c). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/orange_2.png) Release 19.1.6 - Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>This build is for on-premise installations only. For hybrid deployments, hosted instances will keep running the 9032 build. Do not upgrade your marketing instance to the 9035 build as it is not compatible with 9032.

_3 October 2019_

**Improvements**

* Fixed an issue when using the CRM Connector for Salesforce. (NEO-17712)
* Fixed an index issue which could cause performance issues when sending transactional messages.
* Fixed a performance isssue when sending messages. (NEO-17558)
* Fixed an issue which could lead to certain messages not being processed by the Mid-Sourcing server. (NEO-12395)
* Fixed an issue which prevented the full use of the SQL Data Management activity (the "SQL Data Management" named right was missing).

## ![](assets/orange_2.png) Release 19.1.5 - Build 9033{#release-19-1-5-build-9033}

_13 August 2019_

**Improvements**

* Fixed an issue with the SQL statement 'SELECT COUNT' which was executed on the default database rather than the FDA database during Data extraction in Data Management activity.
* To improve customer infrastructure capabilities, an SFTP proxy declaration is now available in the server configuration file.
* Fixed a Client console crash when "adding a linked table" in the Data Loading (RDBMS) workflow activity with no table name. (NEO-12213)
* Fixed an issue with the midEmetter package installation through command line.
* A new authentication option has been added to support OAuth credentials within the AC connector with Microsoft Dynamics. (NEO-11982)
* Fixing issue with UUID (Unique Universal Identifier) cause enrichment activity to fail withHive FDA.

## Release 19.1.4 - Build 9032{#release-19-1-4-build-9032}

![](assets/green_2.png) **April 29th 2020**: new build (9032&#64;3a9dc9c) which includes the following fix:

* Improved security on tracking links in email. This is enabled by default for all customers. An additional, enhanced security feature is available which can be enabled by reaching out to Customer Care. More details on the feature and steps for non-hosted customers to enable it can be found in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).
* Fixed an issue which could prevent images from being displayed on Line deliveries. (NEO-23207)

![](assets/orange_2.png) **March 5th 2020**: new build (9032&#64;19f73c5) which includes the following fix:

* Fixed an issue with external accounts using FTP over SSL. (NEO-20498)

![](assets/orange_2.png) **December 17th 2019**: new build (9032&#64;d6b8062) which includes the following fix:

* Fixed a tracking issue on the following communication channels: mobile (SMS, MMS), push (iOS, Android) and social networks (Facebook, Twitter). (NEO-19595)

![](assets/orange_2.png) **December 11th 2019**: new build (9032&#64;bc4a935) which includes the following fix:

* Fixed a performance isssue when sending messages with a MSSQL database. (NEO-17558)

![](assets/orange_2.png) **November 20th 2019**: new build (9032&#64;3468c7b) which includes the following fixes:

* Fixed a login issue via IMS authentication. (NEO-17312)
* Fixed an issue when displaying cumulative reports on multiple deliveries. (NEO-18165)
* Fixed an issue that could block or make the web server crash.

![](assets/orange_2.png) **September 19th 2019**: new build (9032&#64;cee805c) which includes the following fixes:

* Fixed an issue when using the CRM Connector for Salesforce. (NEO-17712)
* Fixed an index issue which could cause performance issues when sending transactional messages.

![](assets/orange_2.png) **August 13th 2019**: initial 19.1.4 build which includes the following fixes:

* Fixed an issue with the scheduler activity generating undesired error messages during wizard configuration. Reverting update from NEO-11662. (NEO-17097)
* Fixed a regression caused by the NEO-12727 which could lead to workflows being stopped when a Test activity was executed twice. (NEO-16835) 
* Fixed an issue which led to an erroneous HTTP code being returned (HTTP 200 OK instead of HTTP 403 Forbidden) when an invalid or expired session token was used in API calls. (NEO-16826) 
* Fixed an issue with the DKIM key which was not embedded into emails anymore, thus causing deliverability issues. (NEO-16804) 
* Fixed various issues with workflow scheduling. Workflows were scheduled to be executed once a day without taking into account the scheduler configuration. (NEO-16619, NEO-16426)

## ![](assets/orange_2.png) Release 19.1.2 - Build 9029{#release-19-1-2-build-9029}

_21 June 2019_

**Security enhancements**

* To optimize security, the Java library (Netty) has been updated to the latest version (4.1.34). (NEO-12788)

**Improvements**

* Fixed a regression linked to sdomain column management which prevented emails from being sent on certain configurations. 
* To improve performance, a _operation="none" attribute has been added to rtEvent SOAP calls to avoid "SELECT FOR UPDATE" requests.
* Fixed a workflow display issue with outbound transitions after the Test activity. (NEO-12727)
* We now allow the deletion of dummy records created in Microsoft Dynamics during import workflow.
* Improved permissions to execute the security zone package when using internal account.

## ![](assets/orange_2.png) Release 19.1 - Build 9026{#release-19-1-build-9026}

_30 May 2019_

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
   <td> Control Panel<br /> </td> 
   <td> <p>To increase efficiency in your work as an Admin user, manage settings of your SFTP servers by monitoring storage, whitelisting IP addresses, and installing SSH keys for each instance. Please note Control Panel is only available for customers hosted on AWS as of today (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">login through the Experience Cloud today</a>).</p> <p>For more information, refer to the <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">detailed documentation</a> and the <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">how-to video</a>. </p><p>Note: upgrading to the latest Campaign build is not required to access the Control Panel.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit trail<br /> </td> 
   <td> <p>As admin, increase productivity by monitoring and managing changes made within the Adobe Campaign Classic instance. The Audit Trail will log actions made on Source Schemas, Workflows and Options. You can quickly see if an element has been created, modified or deleted.</p><p>For more information, refer to the <a href="../../production/using/audit-trail.md">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">how-to video</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail, Robustness &amp; Scalability<br /> </td> 
   <td> A series of improvements has been added to Campaign Classic. Guardrail, robustness and scalability improvements are listed below.<br /> </td> 
  </tr> 
  <tr> 
   <td> Compatibility Matrix Update<br /> </td> 
   <td> With this new version, Adobe Campaign now supports the following database systems. Refer to the <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Compatibility Matrix</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* For security reasons, you can no longer insert arbitrary commands when using the **[!UICONTROL Pre-process the file]** option in a **[!UICONTROL Data loading (file)]** workflow activity. A drop-down list is now available allowing you to select from 3 options: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) or **[!UICONTROL Decrypt]** (gpg). The XtkSecurity_Disable_Preproc security flag has been added. For new customers, this option will be set to 0. For existing customers, this option will be set to 1 by the postupgrade in order to keep the previous behavior. Refer to this [section](../../workflow/using/data-loading--file-.md).
* Fixed a password visibility issue that occurred when testing the connection of an FDA external account with no time zone set.
* The PDFBox library has been removed.
* Tomcat has been updated to version 7.0.93.
* Fixed a token visibility issue that occurred when the security token was invalid.
* Fixed a potential XTK injection issue in the WSDL JSP (schemawsdl.jsp).
* The credential and password storage in the application's source code and memory has been optimized. 
* PII view restriction has been optimized. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Fixed inconsistency issues in secret key management.
* The same generic error is now displayed for failed login attempts with a valid or invalid username.
* The naming of uploaded files has been enhanced. 
* A new XtkSecurity_Disable_GetSetEnv option has been added to block the use of setEnv and getEnv functions.
* Sensitive information is now hidden in the application stack trace.

**Guardrail, robustness &amp; scalability improvements**

* Lifespan - XtkNewId sequence usage optimization: the most consuming tables have been moved from the xtkNewId sequence to dedicated sequences. [Read more](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) 
* FDA over HTTP v2: the FDA over HTTP protocol is widely used on Hybrid deployments, especially for broadLog retrieval and delivery preparation. Robustness has been enhanced to avoid network issues and possible errors as retrieving or pushing data. This requires that builds at both ends of the connection are up-to-date, otherwise the old protocol will still be used.
* Tracking workflow: the tracking workflow robustness has been enhanced. Several issues related to tracking log inserts/updates and URL tracking customization have been fixed. In addition, the tracking workflow now detects tracking log issues that could lead to errors and stop the workflow. These issues are now discarded and not processed.
* Cleanup workflow: the cleanup workflow has been improved to avoid potential errors and stops. This optimizes database size and performance.
* Embedded images in transactional messages: we have added the full support of embedded images in transactional messages, to avoid possible crashes or missing images.
* Database size - XtkJobLog: a purge mechanism has been added to this table. This has a positive impact on the database size.
* BCC archiving: the default parameters for BCC archiving have been changed to increase archiving velocity. [Read more](../../installation/using/email-archiving.md#parameters)
* Database structure update: SQL requests generated by the Database Structure Update Wizard have been improved for faster execution.
* Guardrails for operator actions: several guardrails have been implemented to prevent operators from performing actions which could impact the platform's integrity. Built-in schemas can no longer be deleted through the interface. Also, the workflow source XML can no longer be edited by non-admin users.
* Two new options have been made available: **XtkSecurity_Restrict_EditXML** (allows you to disable the edition of deliveries’ XML code) and **NmsOperation_OperationMgtDebug** (allows you to monitor the operationMgt technical workflow execution). [Read more](../../installation/using/configuring-campaign-options.md)

**Other changes**

* Push notifications: we now support the Thread ID option for iOS push.
* Improved the management of long name indexes which could cause postupgrade issues.
* Now, during the analysis of a decomail delivery, if the publication mode is set to **[!UICONTROL None]** in the deployment wizard, an error is logged and the analysis is stopped: "Publication mode is set to 'none': Cannot embed image. Images won't be displayed on feature phone." (NEO-12208)
* The broadlog management has been improved for transactional messaging. When broadlogs are synchronized from the execution instance to the control instance, the @lastModified field is updated to the system’s current date. The MC_Update_BlLastModified option has been added for control instances. True means that the current date will be used on the control instance (default behavior). False means that we use the execution instance broadlog’s @lastModified date. (NEO-12579)
* Indexes were added in the coupon temporary tables to optimize delivery sending. (NEO-12437)
* In the Analytics integration, the retrieval of AAM segment data with % character is now allowed. (NEO-12025)
* Removed the 10,000 record limit in Workflow Heatmap to fix a missing data issue. (NEO-12329)
* Open Office is not supported and is now fully removed from the application. If you were still using it, move to Libre Office as it will not work anymore starting 19.1.
* You can now limit Write access to Update data activity in Workflow using sysfilter attributes. [Read more](../../configuration/using/filtering-schemas.md)

**Patches**

* Fixed an issue which prevented the certificate from being uploaded for iOS mobile push notifications.
* Fixed potential recurrent server crashes for transactional push notifications. Other crash issues have been fixed.
* Fixed an issue which caused reporting discrepancies between user activities and tracking reports for the open delivery indicator. (NEO-11742)
* Fixed an issue with the IMS login.
* Fixed an issue which could lead to missing images in a delivery when adding an image from the library. (NEO-11900)
* Fixed an issue that could occur when extracting offer details in a direct mail delivery. (NEO-11700)
* Fixed an issue that could affect SMS transactional message performance. (NEO-9812)
* Fixed a console crash that could occur when using the Defined in an external file option for the main target of a delivery. (NEO-12349)
* Fixed an issue when analyzing a message which targeted recipients for Japanese (.JP) domains. (NEO-12246)
* Fixed a display issue when using a distribution of values with a 1:N link. (NEO-12212, NEO-11820)
* Fixed an issue which could cause NmsMxDomain errors in the MTA logs after a postupgrade. (NEO-12752)
* Fixed an issue when using the "Keep all additional data from the main set" option in an enrichment workflow activity. (NEO-13291)
* Fixed a Tomcat crash issue when sending push notifications using HTTP2. (NEO-12701)
* Fixed an issue with the HTTPRequest API which did not wait for all callbacks to finish. (NEO-12628)
* Fixed an issue with the computing process of tracking indicators for transactional messages. (NEO-12529)
* Fixed an issue with the use of themes in offer management. (NEO-11804)
* Fixed a performance issue when sending push notifications. (NEO-11787)
* FIxed an issue when previewing an outbound XML or CSV file in offer management for a direct mail delivery. (NEO-11290)
* Fixed an issue when installing the **Managing social networks** (Social Marketing) package. (NEO-12081)
* Fixed an issue which prevented you from deleting a web application even if you had the correct access rights. (NEO-12072)
* Fixed an issue which could cause some values to be overwritten when exporting and then importing an object via XML. The XtkExport_IncludeDefaultValues option has been added. When set to True (default behavior), all values are exported. When set to False, modifications are overwritten with the default value. (NEO-11979)
* Fixed an issue which caused the **[!UICONTROL Alert]** workflow activity to fail when an enrichment activity was added after a query. (NEO-12132)
* Fixed an issue on Oracle setups where pipeline (triggers) offsets were not retrieved successfully from the database causing duplicates. (NEO-12121)
* Fixed an issue which could cause diplay errors in pivot tables when using the Analytics integration (NEO-12103)
* Fixed an issue with the Descriptive Analysis report. (NEO-11414)
* Fixed an issue with CRM connectors when the remote table contained a field with an underscore in its name.
* Fixed a issue which could cause a display issue for currency symbols in the Hypothesis reports. (NEO-11634)
* Fixed a redirection and tracking issue when using certain characters in tracking links. 
* Fixed an issue which prevented offer preview from working correctly.
* Fixed an issue with soft bounces not being removed from the address table. 
* Fixed a JAVA error when using barcodes.
* Fixed a translation issue in web applications (NEO-12460)
* Fixed an issue with the s3 File Transfer workflow activity. (NEO-12473)
* Fixed an issue with date fields in web applications. (NEO-12496)
* Fixed an ID exhaustion issue when using seed addresses in a delivery. (NEO-11842)
* Fixed an issue with phantomjs and Debian 9 compatibility.
* Fixed an error when approving the content of a proof. (NEO-12725)
* Fixed an issue with the "Exclude this subset from the population" workflow feature. (NEO-12441)
* Fixed an issue with the HTTPRequest-wait API which did not wait for all callbacks to finish. (NEO-12628)
* Fixed an issue with the "Update Shared Audience" task in a split activity. (NEO-11562)
* Fixed a web server crash issue. (NEO-12904) 
* Fixed an issue with the Nature parameter in transactional templates. (NEO-12334)
* Fixed a console crash issue when displaying the tracked URLs in the email text editor. (NEO-13122)
* Fixed an issue with the Split File activity when importing audiences from Audience Manager. (NEO-11550)
* Fixed an issue which caused errors in the hot click report. (NEO-11459)
* Fixed an issue with offer rendering. (NEO-11565)
* Fixed an issue with the List Update activity when importing audiences from Audience Manager. (NEO-11226)
* Fixed an issue with the Schedule activity and time zone configuration. (NEO-11662)
* Fixed an issue that caused the tracking workflow to fail in case of malformed URLs. 
* Fixed an issue with external accounts after importing the mobile application package.
* Fixed an issue when assigning a time zone to an operator. (NEO-12464)
* Fixed an issue which could cause errors in the mtachild logs. (NEO-11539, NEO-8978)
* Fixed an issue when clicking the History icon in a saved report. (NEO-11620)
* Fixed an issue when editing a pivot table in a report. (NEO-12068)
