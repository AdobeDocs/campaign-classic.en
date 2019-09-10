---
title: Release 19.1.2 - Build 9029
seo-title: Release 19.1.2 - Build 9029
description: Release 19.1.2 - Build 9029
seo-description: 
page-status-flag: never-activated
uuid: 2906cede-687c-444a-b9b5-7d4c45eefdd2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: e6bdf4c4-b7b0-4c1c-b667-2cc12d5192af
index: y
internal: n
snippet: y
---

# Release 19.1.2 - Build 9029{#release-build}

21 June 2019

>[!CAUTION]
>
>This build has been recalled. Please [upgrade to the latest build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) or contact [technical support](https://support.neolane.net/).

## Security enhancements {#security-enhancements}

* To optimize security, the Java library (Netty) has been updated to the latest version (4.1.34). (NEO-12788)

## Improvements {#improvements}

* Fixed a regression linked to sdomain column management which prevented emails from being sent on certain configurations. 
* To improve performance, a _operation="none" attribute has been added to rtEvent SOAP calls to avoid "SELECT FOR UPDATE" requests.
* Fixed a workflow display issue with outbound transitions after a Test activity. (NEO-12727)
* We now allow the deletion of dummy records created in Microsoft Dynamics during import workflow.
* Improved permissions to execute the security zone package when using internal account.

