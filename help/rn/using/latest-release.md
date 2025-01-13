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

## Release 7.4.1 - Build 9383 {#release-7-4-1}

[!BADGE General Availability]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="General Availability"}

_June 18, 2024_

### Changes and improvements {#release-7-4-1-changes}

* With the Service Account (JWT) credential being deprecated by Adobe, Campaign outbound integrations with Adobe solutions and apps now rely on OAuth Server-to-Server credential. If you have implemented outbound integrations, such as Campaign-Analytics integration or Experience Cloud Triggers integration, you must upgrade your Campaign environment to v7.4.1 and migrate your Technical Account to oAuth before January 27, 2025. [Learn more](../../integrations/using/oauth-technical-account.md)

* Once you have [migrated your Campaign technical operators to Developer Console](../../technotes/using/ims-migration.md) and [transitioned to IMS for end-user authentication](../../technotes/using/migrate-users-to-ims.md), you can now enable the user interface and API restrictions to remove options and capabilities which are specific to native authentication. [Learn more](../../technotes/using/impact-ims-migration.md)


### Compatibility updates {#release-7-4-1-compat}

The [compatibility matrix for Adobe Campaign](compatibility-matrix.md) has been updated with changes coming with this new release, and listed below.

* Adobe Campaign is now compatible with **Microsoft Server 2022** as operating system.
* Adobe Campaign is now compatible with **RHEL 9** as operating system.

    >[!CAUTION]
    >
    >As an on-premise customer using RHEL 9, if you want to use DKIM/Domain keys, you must update your system settings as detailed in [this section](../../installation/using/installing-packages-with-linux.md#rhel-9-update).


* Adobe Campaign is now compatible with **Microsoft SQL Server 2022** and **Oracle 23c** as Relation Database Management Systems, and in Federated Data Access (FDA).

* Adobe Campaign now requires at least a Java Development Kit (JDK) 11. On Windows, the JRE must be available as described in [this section](../../installation/using/application-server.md#jdk).

* The Campaign (Neolane) SDK for mobile applications is now deprecated. You must now transition to Adobe Experience Platform SDK. [Learn more](deprecated-features.md).
    
    In the meantime, to ensure service continuity, Campaign v7.4 comes with:
    
    * a new Campaign SDK 1.0.27 for iOS, compatible with iOS 16 and 17, and the latest [Apple iOS Privacy Request requirements](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
    * a new Campaign SDK for Android 14.

### Other changes {#release-7-4-1-other}

Starting v7.4.1, XML libraries for RPM Linux packages are no longer included in Campaign. As an on-premise or hybrid customer, your Administrator must install these librairies. [Learn more](../../installation/using/installing-packages-with-linux.md)

### Patches {#release-7-4-1-patches}

This release comes with the following fixes:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592 

