---
title: Release 19.2
seo-title: Release 19.2
description: Release 19.2
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

# Release 19.2{#release-19-2}

## Release 19.2 - Build XXX{#release-19-2-build-XXX}

28 October 2019

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
   <td> California Consumer Privacy Act (CCPA)<br /> </td> 
   <td> <p>CCPA is the State of California’s new privacy law that harmonizes and modernizes data protection requirements going into effect on Jan 01, 2020. CCPA applies to Adobe Campaign customers who hold data for Data Subjects residing in California.</p>
    <p>In addition to the privacy capabilities already available (including consent management, data retention settings, and user roles), Adobe Campaign helps facilitate your readiness for CCPA:</p>
    <ul>
      <li>Right to Access and Right to Delete: we are leveraging the capabilities that were added for GDPR. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Read more</a></li>
      <li>You have the possibility to track whether a consumer has opted-out for the sale of Personal Information. For this, you need to extend the Profiles table and add an **Opt-Out for CCPA field**. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Read more</a></li></td> 
  </tr> 
    <tr> 
   <td> Workflow live monitoring<br /> </td> 
   <td> <p>You can now monitor the execution status of all workflows on your instance using predefined views.</p></td> 
  </tr> 
  <tr> 
   <td> Support New AMP email format (public beta)<br /> </td> 
   <td> Adobe Campaign enables you to try out the new interactive <a href="https://amp.dev/about/email/">AMP for Email</a> format, which allows marketers to include AMP components inside messages to enhance the email experience with rich, dynamic and interactive content, directly actionable in the message itself.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

**Improvements**

* Memory consumption optimization for Push Notifications.
* For performance and storage optimization, the handling of the logins.log file has been enhanced. The file is now split into multiple files, one each day with a maximum of 365 files retained. [Read more](../../production/using/log-files.md)
* The **WdbcOptions_TempDbName** option has been added to configure a separate database for working tables on Microsoft SQL Server. This optimizes backups and replication. [Read more](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
* Microsoft Dynamics CRM external account can now be configured using password credentials (password + username) or certificate (private key).
* Some enhancements have been added to the Hadoop FDA connector to improve reliability
* The **XtkCleanup_NoStats** option has been enhanced for PostgreSQL to better control the behavior of the storage optimization step of the cleanup workflow. [Read more](../../production/using/database-cleanup-workflow.md#statistics-update)
* A specific guardrail has been added to check disk space before allowing to upload public resources on the server.
* A new **WdbcKillSessionPolicy** configuration option is available allowing you to affect Unconditional Stop behavior on all the workflows and PostgreSQL database queries.
* A specific guardrail has been added to prevent installation of packages which are not compatible with the Campaign instance
* A new Campaign option has been added: **NmsOperation_DeliveryPreparationWindow**. It allows you to define the number of days above which deliveries with inconsistent status will be excluded from the count of running deliveries.
* An account lockout mechanism has been added to the **logon()** API. It prevents any further login attempts after a certain number of consecutive failed login attempts within a specified time frame.
* A new option in the delivery properties allows to define a time-out period for the personalization run time, in order to avoid the personalization phase to run for too long.
* The "ftp" protocol option has been added to allow you to use a proxy configuration for SFTP connections. [Read more](../../installation/using/{#configuring-campaign-server.md#proxy-connection-configuration)

**Other changes**

* Apache 2.2 and Centos 6 are now deprecated for Campaign Classic implementations. [Read more](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**Patches**

