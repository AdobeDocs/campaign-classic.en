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

## Release 7.4.1 - Build XXX {#release-7-4-1}

[!BADGE General Availability]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="General Availability"}


_June 18, 2024_

### Changes and improvements {#release-7-4-1-changes}

* If you are using Adobe Identity Management Service (IMS) to connect to Adobe Campaign, you can now deactivate options which are specific to native authentication. [Learn more](../../campaign-classic-home.md)

* With the Service Account (JWT) credential being deprecated by Adobe, Campaign outbound integrations with Adobe solutions and apps now rely on OAuth Server-to-Server credential. If you have implemented outbound integrations, such as Campaign-Analytics integration or Experience Cloud Triggers integration, you must upgrade your Campaign environment to v7.4.1 and migrate your Technical Account to oAuth before January 27, 2025. [Learn more](../../campaign-classic-home.md)


### Compatibility updates {#release-7-4-1-compat}

The [compatibility matrix for Adobe Campaign](compatibility-matrix.md) has been updated with changes coming with this new release, and listed below.

* Adobe Campaign is now compatible with **Microsoft Server 2022** and **RHEL 9** as operating systems.

* Adobe Campaign is now compatible with **Microsoft SQL Server 2022**, **Oracle 23c**, **PostgreSQL 15 and 16** as a Relation Database Management Systems.

* You can now connect in Federated Data Access (FDA) to **Microsoft SQL Server 2022** and **Oracle 23c**.

* The Campaign (Neolane) SDK for mobile applications is now deprecated. You must now transition to Adobe Experience Platform SDK. [Learn more](deprecated-features.md).
    
    In the meantime, to ensure service continuity, Campaign v7.4 comes with:
    
    * a new Campaign SDK 1.0.27 for iOS, compatible with iOS 16 and 17, and the latest [Apple iOS Privacy Request requirements](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
    * a new Campaign SDK for Android 14.



### Patches {#release-7-4-1-patches}

This release comes with the following fixes:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592 

