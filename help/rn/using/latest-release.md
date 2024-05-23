---
product: campaign
title: Latest Release
description: Latest Campaign Classic v7 Release Notes
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
---
# Latest release{#latest-release}

This page lists new capabilities, improvements and fixes coming with the **latest Campaign Classic v7 Release**. Every new build comes with a status which is materialized by a color. Learn more about Campaign Classic v7 build statuses in [this page](rn-overview.md). 

## Release 7.3.5 - Build 9368 {#release-7-3-5}

[!BADGE General Availability]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="General Availability"}


_December 5, 2023_


### Security enhancements {#release-7-3-5-security}


* With Campaign Classic v7.3.5, the authentication process has been improved and secured. Technical operators should now use Adobe Identity Management System (IMS) to connect to Campaign. Learn how to migrate your existing technical account(s) in [this technote](../../technotes/using/ims-migration.md).
  
* In addition, as part of the effort to reinforce security and authentication process, Adobe Campaign highly recommends to migrate end user authentication mode from the login/password native authentication to Adobe Identity Management System (IMS). Learn how to migrate your operators in [this technote](../../technotes/using/migrate-users-to-ims.md).

* Now, when a web form has the **Pending publication** status, it does not become automatically live. To prevent security issues, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Patches {#release-7-3-5-patches}

* Fixed an issue when using data from a Google Big Query database and updating data in an Oracle database: all keys were set to `0` in the workflow temporary table. (NEO-65091)
* Fixed an issue which was causing a workflow execution to fail when two queries on a Google Big Query database were combined in a **Union** workflow activity. (NEO-63705)
* Fixed an issue which was requesting the user to re-authenticate when clicking the `Back` button in a Campaign report. (NEO-65087)
* Fixed an error in the Database Cleanup workflow which was happening when a delivery was deleted before its delivery proofs. (NEO-48114)
* Fixed an issue while connecting to the Client Console: recent updates on TLS verification were leading to connection error. (NEO-50488)
* Fixed an issue with the HTTP Proxy authentication after Campaign postupgrade to 7.3.1. HTTP requests in Campaign workflows were failing with `error 407 – proxy auth required is returned`. (NEO-49624)
* Fixed an intermitent failure with GPG decryption in **Script** workflow activities. The associated error message was: `gpg: decryption failed: No secret key`. (NEO-50257)
<!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

