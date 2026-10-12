---
title: Migrate Campaign operators to Adobe Identity Management System (IMS)
description: Learn how to migrate Campaign operators to Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Migrate Campaign operators to Adobe Identity Management System (IMS) {#migrate-users-to-ims}

As part of the effort to reinforce security and authentication process, Adobe Campaign highly recommends to migrate end user authentication mode from the login/password native authentication to Adobe Identity Management System (IMS). All operators should implement [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} to connect to Campaign.

Learn more about this migration in [this page](ac-ims.md).

## What changed? {#move-to-ims-changes}

With Campaign Classic, all regular users can already connect to the Adobe Campaign client console using their Adobe ID, through Adobe Identity Management System (IMS). However, user/password connections are still available. This will no longer be permitted with Campaign v8.

In addition, as part of the effort to reinforce security and authentication process, Adobe Campaign client application now calls Campaign APIs directly using the IMS technical account token. Migration for technical operators is detailed in a dedicated article, available in [this page](ims-migration.md).

This change is already applicable in Campaign Classic v7, and will be **mandatory** to move to Campaign v8. 

Adobe supports you in this migration effort. You can find detailed context and step by step guidelines in the below article.

## Are you impacted?{#migrate-ims-impacts}

This procedure applies to all Campaign users which are not already connecting to Campaign with their Adobe ID.

If operators in your organization are connecting to Campaign client console using their login/password (aka. native authentication), you are impacted, and should migrate these operator(s) to Adobe IMS as detailed below.

Migration to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is a security imperative to make your environments secure and standardized, as most of the other Adobe Experience Cloud solutions and apps are already on IMS.

This change is applicable starting Campaign Classic v7.4.1 (and latest [IMS migration compatible versions](ac-ims.md#ims-versions)) and is **mandatory** to move to Adobe Campaign v8.

>[!IMPORTANT]
>
>**Control Panel access impact**
>
>Once you migrate your users to IMS, be aware that any Product Profile in the Adobe Admin Console containing the word "admin" in its name (such as "Administrators", "admin", "admins", "approval admin", etc.) will automatically grant access to the Campaign Control Panel. Control Panel is a self-service tool that allows making significant changes to Campaign instances. 
>
>Carefully review your Product Profile naming conventions to ensure only authorized users have access to Control Panel. Learn more about managing Control Panel permissions in the [Control Panel documentation](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.


## How to migrate Hybrid and On-premise environments? {#ims-migration-procedure-on-prem}

Key steps for this migration are listed below: 

1. Upgrade your environments to Campaign v7.4.1 (or an [IMS migration compatible version](#ims-versions)).
1. After the upgrade, you can still create new users with both methods, as native user or with IMS.
1. Your internal Campaign Administrator must configure Adobe IMS as detailed in [this section](../../integrations/using/configuring-ims.md).
1. Then add unique emails to all native users on the Campaign client console. This step is detailed in [this section](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"} (Campaign v8 documentation).
1. Create users and product profiles in Adobe Admin Console as detailed in [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Enable the **Connect with Adobe ID** option for all operators.
1. Implement Adobe IMS for your connection as detailed in [this page](../../integrations/using/implementing-ims.md).

You can also migrate your technical operator(s) to Adobe Developer Console as detailed in [this technote](ims-migration.md). 

## Frequently Asked Questions {#ims-migration-faq}

For answers to common questions about the migration (creating users after the migration, adding emails for native users, logging in via IMS, downtime, organizations already using IMS, viewing the operators' authentication type), refer to the [Campaign v8 technote](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank} (Campaign v8 documentation).

>[!MORELIKETHIS]
>
>* [Migration of technical users to Adobe Developer console](ims-migration.md)
>* [Adobe Campaign Classic v7 release notes](../../rn/using/latest-release.md)
>* [What is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
