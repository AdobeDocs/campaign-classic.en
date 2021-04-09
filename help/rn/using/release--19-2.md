---
solution: Campaign Classic
product: campaign
title: Release 19.2
description: Release notes for Campaign 19.2
feature:
role: 
level:
exl-id: 3c529e4e-8787-41d2-b85d-3feaa5432196
---
# Release 19.2{#release-19-2}

## ![](assets/do-not-localize/limited_2.png) Release 19.2.4 - Build 9082 {#release-19-2-4-build-9082}

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

## ![](assets/do-not-localize/red_2.png) Release 19.2.3 - Build 9081 {#release-19-2-3-build-9081} 

_February 7, 2020_

**Improvements**

* Fixed a regression issue due to the implementation of SSL certification which caused the user connection to fail on Windows server. (NEO-20629)
* Fixed an issue which displayed an incorrect version tag number in the **About** menu.

## ![](assets/do-not-localize/red_2.png) Release 19.2 - Build 9080 {#release-19-2-build-9080} 

_December 2, 2019_

**What's new?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA is the State of California’s new privacy law that harmonizes and modernizes data protection requirements going into effect on Jan 01, 2020. CCPA applies to Adobe Campaign customers who hold data for Data Subjects residing in California.</p>
    <p>In addition to the privacy capabilities already available (including consent management, data retention settings, and user roles), Adobe Campaign helps facilitate your readiness for CCPA:</p>
    <ul>
      <li>Right to Access and Right to Delete: we are leveraging the capabilities that were added for GDPR. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Read more</a></li>
      <li>You can track whether a consumer has opted-out for the sale of Personal Information. For this, you need to extend the Profiles table and add an <strong>Opt-Out for CCPA</strong> field. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Read more</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Workflow live monitoring</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>You can now monitor the execution status of all workflows on your instance using predefined views.</p>
   <p>For more information, refer to the <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">detailed documentation</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Interactive content with AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign enables you to try out the new interactive <a href="https://amp.dev/about/email/">AMP for Email</a> format, which allows marketers to include AMP components inside messages to enhance the email experience with rich, dynamic and interactive content, directly actionable in the message itself.</p>
   <p>This capability is released as a public beta.</p>
   <p>For more information, refer to the <a href="../../delivery/using/defining-interactive-content.md">detailed documentation</a> and the <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">tutorial video</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Secure SMS Messaging (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Secured SMS is now supported through the Extended Generic SMPP Connector. This allows an encrypted connection to the provider.</p> <p><strong>Warning</strong> This feature requires an up-to-date certificate on all servers. Invalid, revoked or expired certificates will generate errors affecting the overall SMS sending capabilities.</p><p>For more information, refer to the <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html">detailed documentation</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* Fixed Stored Cross Site Scripting vulnerabilities in Campaign interface – input data validation and output encoding. (NEO-16810)
* Fixed a security issue on profile authorization which could allow access to unauthorized data, by reinforcing login restriction policy. (NEO-14445)

**Improvements**

* Memory consumption optimization for Push Notifications.
* For performance and storage optimization, the handling of the **logins.log** file has been enhanced. The file is now split into multiple files, one each day with a maximum of 365 files retained. [Read more](../../production/using/log-files.md)
* Microsoft Dynamics CRM external account can now be configured using password credentials (password + username) or certificate (private key). [Read more](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Some enhancements have been added to the Hadoop FDA connector to improve reliability
* A specific guardrail has been added to check disk space before allowing to upload public resources on the server.
* New [Campaign Options](../../installation/using/configuring-campaign-options.md) have been added:
    * The **WdbcKillSessionPolicy** configuration option allows you to affect **Unconditional Stop** behavior on all the workflows and PostgreSQL database queries. 
    * The **NmsOperation_DeliveryPreparationWindow** option allows you to define the number of days above which deliveries with inconsistent status will be excluded from the count of running deliveries.
    * The **WdbcOptions_TempDbName** option allows you to configure a separate database for working tables on Microsoft SQL Server. This optimizes backups and replication. [Read more](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
    * The **XtkCleanup_NoStats** option has been enhanced for PostgreSQL to better control the behavior of the storage optimization step of the database cleanup workflow. [Read more](../../production/using/database-cleanup-workflow.md#statistics-update)
* An account lockout mechanism has been added to the **logon()** API. It prevents any further login attempts after a certain number of consecutive failed login attempts within a specified timeframe.
* A new **Maximum personalization run time** option in the delivery properties allows you to define a time-out period for the personalization run time, in order to prevent the personalization phase from running for too long. [Read more](../../delivery/using/personalization-fields.md#timing-out-personalization)
* The **ftp protocol** option has been added to allow you to use a proxy configuration for SFTP connections. [Read more](../../installation/using/file-res-management.md)
* New support of proxy access to an SFTP external server for on-premise environments.
* A specific guardrail has been added to prevent installation of packages which are not compatible with the Campaign instance. [Read more](../../installation/using/installing-campaign-standard-packages.md)

_Deprecated systems_

The following systems are now [deprecated](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) for Campaign Classic implementations:
* Apache 2.2 
* Centos 6 

Please ensure you are on supported versions of any systems listed in the latest Campaign Compatibility matrix. [Read more](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

The build 1.0.26 of the iOS SDK is now available. In this new build, we’ve added the support of iOS 13. This new version now supports notification priority and the new registration token management process for iOS 13 Push notifications. If you’re running applications on a previous version of the SDK, you need to recompile your applications with the new SDK. To get the SDK, please contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Patches**

* Fixed a crash issue when the **Add linked table** field was empty in the **Data Loading (RDBMS)** workflow activity. (NEO-12213)
* Fixed an issue which could lead to certain messages not being processed by the Mid-Sourcing server. (NEO-12395)
* Fixed an issue in the database cleanup workflow when using the query banding option with Teradata. (NEO-12399)
* Fixed an issue affecting delivery analysis with typology rule including ne.jp domain. (NEO-12609)
* Fixed an issue related to SMS over TLS updates which were implying to a more restrictive certificate policy. These updates could lead to a connection failure between marketing and mid-sourcing servers in case of an out-of-date certificate. (NEO-17698) 
* Fixed an issue when using the **Test connection** button on an external account in a mid-sourcing environment with Vault authentication. (NEO-12722)
* Fixed an issue on queries using date functions with an FDA Hadoop connection. (NEO-12847)
* Fixed an issue when replacing an image in the email editor. (NEO-13098)
* Fixed an issue which could lead to post-upgrade errors on folders which had been deleted or moved to another location. (NEO-13118)
* Fixed an issue on image display when using the **Define image per device screen size** option on LINE messages. (NEO-13228)
* Fixed a delivery preparation issue when the **Exclude duplicate address during delivery** option is unselected. (NEO-13240)
* Fixed an issue in workflows when using the **File transfer** activity to download files using the **Delete the source files after transfer** option, with name containing a space character. (NEO-13411)
* Fixed an issue with Tomcat cache cleanup which could lead to memory issues. (NEO-13456)
* Fixed an issue when installing the **Control of offer engine with execution instance** built-in package on an existing control instance running in Microsoft SQL 2017. (NEO-13539)
* Fixed a console crash issue that could occur when unchecking tracked URLs in an email, from the **Text content** tab due to a non-initialized variable. (NEO-13545)
* Fixed an encoding issue on Chinese sender name. (NEO-13837)
* Fixed an error which could raise when displaying survey response data from the Explorer. (NEO-14590)
* Fixed an issue which could lead to discrepancy between the delivery log classification and the quarantine table. (NEO-16547)
* Fixed an issue with DKIM keys which were not embedded into emails. (NEO-16804)
* Fixed an issue which was displaying the wrong error code when an invalid session token was used in the context of API calls to trigger events. The error code was 'HTTP 200 OK' instead of 'HTTP 403 Forbidden'. (NEO-16826)
* Fixed an issue when displaying delivery reports via web access. (NEO-17015)
* Fixed an IMS authentication issue when login to Adobe Campaign. (NEO-17312)
* Fixed an issue which prevented quarantined emails from being deleted by the Privacy Management process. (NEO-17314)
* Fixed throughput issues after upgrading to 9031 with SQL database. (NEO-17558)
* Fixed an issue which affected the CRM Connector with Salesforce. (NEO-17712)
* Fixed a timeout issue when importing data from an external SFTP. (NEO-19723)
* Fixed an issue when accessing to Predictive models. (NEO-19713)
* Fixed an issue affecting random sampling in **Split** workflow activity with Hadoop FDA database. (NEO-16636)
* Fixed a regression on Oracle causing some functions to be considered as invalid after postupgrade. (NEO-12759)
