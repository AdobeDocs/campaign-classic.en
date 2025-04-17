---
product: campaign
title: Latest Release
description: Latest Campaign Classic v7 Release Notes
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
---
# Latest release {#latest-release}

This page lists new capabilities, improvements and fixes coming with the **latest Campaign Classic v7 Release**. Every new build comes with a status which is materialized by a color. Learn more about Campaign Classic v7 build statuses in [this page](rn-overview.md). 

## Release 7.4.2 - Build 9390 {#release-7-4-2}

[!BADGE General Availability]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="General Availability"}

_April 2, 2025_  

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

--> 

### Security improvements {#security-7-4-2}

This release comes with several security fixes.

Connection with Adobe solutions and apps through the **[!UICONTROL Adobe Experience Cloud]** external account has been updated to reinforce security.

### Fixes {#release-7-4-2-fixes}

This release comes with the following main fixes:

* TLS / SMPP connection - Fixed SMPP stability issues

* Google BigQuery fixes:

    * Fixed regressions on BOOLEAN data types
    * Fixed proxy settings issues
    * Fixed regressions on DATETIME data types
    * Fixed bulk load stability
    * Improved internal tests on ODBC versions
    * Fixed an issue with special characters on connection string
    * Removed default timeout (5min) on Google BigQuery queries

* Mail Transfer Agent (MTA) - Fixed orphan MTA child to be stuck on **[!UICONTROL Start pending]** status.

The following issues are also fixed in this release:

* Fixed an issue where the Data Loading (file) activity failed to upload files to the server after an upgrade to version 8.3.8. Users can now successfully upload files without encountering stuck progress or console errors. (NEO-47269)

* Resolved segmentation fault errors in Apache following an upgrade to Adobe Campaign Classic 7.2.2 build 9349. This fix prevents core file generation and ensures stable server operation. (NEO-59059)

* Addressed a connectivity issue with the BigQuery database after upgrading to version 7.3.3 build 9359. Users can now test connections successfully using the GCP external account. (NEO-62455)

* Enhanced compatibility for Boolean and Datetime column updates in Google BigQuery tables using FDA. This fix ensures proper handling of data types during Insert/Update operations. (NEO-65774)

* Fixed a resource injection vulnerability that allowed attackers to inject HTML elements into email endpoints. This security enhancement prevents unauthorized access and phishing attempts. (NEO-66462)

* Resolved intermittent errors when inserting data into BigQuery tables due to HTTP content or transfer encoding issues. This fix ensures stable data loading workflows. (NEO-66989)

* Addressed a path traversal vulnerability in the `File.list()` method within workflows. This security enhancement prevents unauthorized directory access and protects sensitive files. (NEO-77898)

* Fixed an issue where SMS delivery logs were not updating correctly to "received on mobile" status. This enhancement ensures accurate delivery reporting. (NEO-78843)

* Resolved login errors in Adobe Campaign Classic when using Azure Federated Access. Users can now log in successfully via the client console. (NEO-79373)

* Fixed a crash in workflows caused by the `CCurlAzureBlobStorage::UploadStream()` method. This enhancement ensures stable workflow execution. (NEO-79598)

* Activated two critical compilation flags (ControlFlowGuard and StackProtection) on Windows to enhance product security and mitigate exploitation risks. (NEO-80145)

* Fixed an issue where event statuses were sent incorrectly while the broadlog was in a failed state. This enhancement ensures accurate event reporting. (NEO-80245)

* Enhanced the BigQuery FDA connector by allowing users to adjust the timeout period for queries. This improvement prevents timeout errors during long-running queries. (NEO-81222)

* Updated the Campaign 7.4.1 release upgrade process to include required dependencies. This enhancement simplifies the upgrade process for users. (NEO-81433)

* Fixed a console crash issue when using a subworkflow in combination with an enum field. This enhancement ensures stable workflow execution. (NEO-81864)

* Resolved an issue where MTA child processes were stuck, blocking delivery slots. This fix ensures smooth delivery operations for Push and WhatsApp communications. (NEO-82351)

* Fixed an issue where deliveries were stuck in personalization pending due to paused delivery activities. This enhancement ensures successful delivery execution. (NEO-82781)

* Enhanced IMS login functionality by leveraging the CampaignIO endpoint for authentication. This improvement streamlines the login process. (NEO-82838)

* Readdressed BigQuery FDA timeout errors to ensure stable query execution post-hotfix deployment. (NEO-82923)

* Resolved a space issue when loading large data volumes into Teradata tables. This enhancement ensures stable data loading operations. (NEO-83252)

* Fixed an issue where GCP queries failed due to mismatched date and timestamp comparisons after upgrading to version 9383. This enhancement ensures query compatibility. (NEO-83826)

* Addressed delivery failures caused by resuming paused delivery activities. This fix ensures successful delivery execution. (NEO-83809)

* Fixed authentication errors with the Snowflake FDA connector when using Private Key Authentication. This enhancement ensures successful database connections. (NEO-84024)

* Implemented watchdog changes to address MTA child slot blockage caused by stuck processes. This enhancement ensures smooth delivery operations. (NEO-84553)

* Augmented JS wait checks to address MTA child slot blockage caused by processes in a working state. This fix ensures stable delivery operations. (NEO-85150)