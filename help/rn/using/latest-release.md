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

>[!AVAILABILITY]
>
>This release is in **Limited Availability** (LA). It is restricted to Hosted/Managed services users only. This release will soon be available for hybrid and on-premise customers. 

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

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150
 
