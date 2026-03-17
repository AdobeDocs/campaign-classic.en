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

## Release 7.4.3 - Build 9394 {#release-7-4-3}

[!BADGE General Availability]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="General Availability"}

_March 16, 2026_  

>[!CAUTION]
>
> Client Console upgrade is mandatory.

### Security improvements {#security-7-4-3}

* To maintain optimal security, stability, and compliance, Debian has been upgraded to version 13 and PostgreSQL to version 17. Refer to the [compatibility matrix](compatibility-matrix.md).

### Fixes {#fixes-7-4-3}

* Fixed an issue where the barcode component allowed an unbounded height parameter, which could lead to a security vulnerability. (NEO-89984)
* Fixed an issue where enumeration fields in lists created via workflows were missing temporary name attributes, causing incorrect or blank enum labels to be displayed in the interface. (NEO-91158)
* Fixed an issue where delivery statistics were not fully recomputed for some deliveries, particularly affecting the success indicators. (NEO-88106)
* Fixed an issue where delivery preparation failed with personalization errors when using targetData fields in workflows with deduplication activities. (NEO-87693)
* Fixed an issue where concatenating single-character string fields with other strings failed in PostgreSQL 15 due to type casting requirements. (NEO-88028)
* Fixed an issue where tracking logs for collaborative campaigns in Distributed Marketing were not being written to the database due to a mismatch between parent and child delivery IDs. (NEO-86836)
* Fixed an issue where delivery logs showed messages as canceled even though they were successfully sent, particularly affecting deliveries with wave scheduling. (NEO-78933)
* Fixed an issue where the database cleanup workflow was not efficiently purging data, which could impact performance. (NEO-76439)

