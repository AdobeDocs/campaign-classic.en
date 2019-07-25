---
title: Release 19.1.2 - Build 9029
seo-title: Release 19.1.2 - Build 9029
description: Release 19.1.2 - Build 9029
seo-description: 
page-status-flag: never-activated
uuid: 9023cd4f-29f4-44fc-866b-f2f0cf6ee6d5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: rn
discoiquuid: 7aea2b17-5244-465c-a7ec-4efc9c7d30a7
index: y
internal: n
snippet: y
---

# Release 19.1.2 - Build 9029{#release-build}

21 June 2019

## Security enhancements {#security-enhancements}

* To optimize security, the Java library (Netty) has been updated to the latest version (4.1.34). (NEO-12788)

## Improvements {#improvements}

* Fixed a regression linked to sdomain column management which prevented emails from being sent on certain configurations. 
* To improve performance, a _operation="none" attribute has been added to rtEvent SOAP calls to avoid "SELECT FOR UPDATE" requests.
* Fixed a workflow display issue with outbound transitions after a Test activity. (NEO-12727)
* We now allow the deletion of dummy records created in Microsoft Dynamics during import workflow.
* Improved permissions to execute the security zone package when using internal account.

