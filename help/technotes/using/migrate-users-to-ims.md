---
title: Migrate Campaign operators to Adobe Identity Management System (IMS)
description: Learn how to migrate Campaign operators to Adobe Identity Management System (IMS)
---
# Migrate Campaign operators to Adobe Identity Management System (IMS) {#migrate-users-to-ims}

As part of the effort to reinforce security and authentication process, Adobe Campaign highly recommends to migrate end user authentication mode from the login/password native authentication to Adobe Identity Management System (IMS). All operators should implement [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} to connect to Campaign. 

Note that in Campaign v8, connecting with user/password (aka native authentication) will no longer be allowed. **Adobe recommends to perform this migration in Campaign v7.3.5 to be able to migrate smoothly to Campaign v8.**

This article details the steps required to migrate a technical operator to technical account on Adobe Developer console.

## What changed?{#move-to-ims-changes}

With Campaign Classic, all regular users can already connect to the Adobe Campaign client console using their Adobe ID, through Adobe Identity Management System (IMS). However, user/password connections are still available. This will no longer be permitted with Campaign v8.

In addition, as part of the effort to reinforce security and authentication process, Adobe Campaign client application now calls Campaign APIs directly using the IMS technical account token. Migration for technical operators is detailed in a dedicated article, available in [this page](ims-migration.md).

This change is already applicable in Campaign Classic v7, and will be **mandatory** to move to Campaign v8. 

## Are you impacted?{#migrate-ims-impacts}

This procedure applies to all Campaign users which are not already connecting to Campaign with their Adobe ID.

If operators in your organization are connecting to Campaign client console using their login/password (aka. native authentication), you are impacted, and should migrate these operator(s) to Adobe IMS as detailed below.

Migration to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is a security imperative to make your environments secure and standardized, as most of the other Adobe Experience Cloud solutions and apps are already on IMS.

## How to migrate Hosted and Managed Services environments? {#ims-migration-procedure}

### Prerequisites {#ims-migration-prerequisites}

Before starting the migration process, you must reach out to your Adobe Transition Manager (for Managed Services customers), or to Adobe Customer Care (for other hosted customers), so that Adobe technical teams can migrate your existing Operator groups and Named rights to Adobe Identity Management System (IMS).

### Key steps {#ims-migration-steps}

Key steps for this migration are listed below: 

1. Adobe upgrades your environments to Campaign v7.3.5.
1. After the upgrade, you can still create new users with both methods, as native user or with IMS.
1. Your internal Campaign Administrator must add unique emails to all native users on the Campaign client console, and confirm to your Adobe representative / Customer Care once this is done.  This step is detailed in [this section](#ims-migration-id).
1. Work with your Adobe representative / Customer Care to secure a date for Adobe to run automated migration for your non-technical users (operators) and product profiles. This step requires an hour window with no downtime to any of your services.
1. Your internal Campaign Administrator validates these changes, and provides sign-off. After this migration, you must no longer create any further operator authenticating with his login and password.

You can also migrate your technical operator(s) to Adobe Developer Console as detailed in [this technote](ims-migration.md). 

Once this migration is completed, confirm to your Adobe Transition Manager (for Managed Services users), or to Adobe Customer care (for Hosted customers). Adobe then marks the migration as complete. Your environment is then secured and standardized. 


## How to migrate Hybrid and On-Premise environments? {#ims-migration-procedure-on-prem}

Key steps for this migration are listed below: 

1. Upgrade your environments to Campaign v7.3.5.
1. After the upgrade, you can still create new users with both methods, as native user or with IMS.
1. Your internal Campaign Administrator must configure Adobe IMS as detailed in [this section](../../integrations/using/configuring-ims.md).
1. Then add unique emails to all native users on the Campaign client console. This step is detailed in [this section](#ims-migration-id).
1. Create users and product profiles in Adobe Admin Console as detailed in [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Enable the **Connect with Adobe ID** option for all operators.
1. Implement Adobe IMS for your connection as detailed in [this page](../../integrations/using/implementing-ims.md).

You can also migrate your technical operator(s) to Adobe Developer Console as detailed in [this technote](ims-migration.md). 


## Frequently Asked Questions {#ims-migration-faq}

### When can I start the migration? {#ims-migration-start}

A recommendation for the migration to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is to upgrade your environment to Campaign Classic v7.3.5.

You can start IMS migration on your stage environment, once it is upgraded to Campaign Classic v7.3.5, and accordingly plan for production environment.

### What happens after build upgrade to Campaign Classic v7.3.5? {#ims-migration-after-upgrade}

After your environments have been upgraded to Campaign Classic v7.3.5, you can initiate your transition to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}. 

### When is the migration complete? {#ims-migration-end}

Once end-user migration and technical user migration to Adobe Identity Management System (IMS) is done, you must contact your Adobe representative / Customer Support so that Adobe can mark your migration as complete.

### How to create users after migration? {#ims-migration-native}

Adobe recommends to create only IMS users after upgrading to Campaign Classic v7.3.5.

As a Campaign Administrator, you can grant permissions to the users of your organization through Adobe Admin Console and Campaign Client Console. Users log on to Adobe Campaign with their Adobe ID. Learn how to set up permissions with IMS in [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}. 

### How to add emails for current native users? {#ims-migration-id}

As a Campaign Administrator, you must add email IDs to all native users from the client console. To perform this, follow the steps below:

1. Connect to the client console and browse to **Administration > Access Management > Operators**.
1. Select the operator to update in the operator list.
1. Enter the email of the operator in the **Contact points** section of the operator form.
1. Save your changes.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### How to log in to Campaign via IMS? {#ims-migration-log}

Learn how to connect to Campaign with your Adobe ID in [this section](../../integrations/using/implementing-ims.md).

### Will there be a downtime during this migration? {#ims-migration-downtime}

For Hosted and Managed Services customers, to finalize the migration (migrate users and product profiles), Adobe requires one hour window with no downtime to any of your instances (workflows, etc).

During this timeframe, all Campaign users need to log off, and log back with their Adobe ID once the migration to IMS is finalized.

Adobe strongly recommends all users should be logged off during the migration window.

### Users in my organization are already using IMS, do I still need to perform IMS migration?{#ims-migration-needed}

There are 2 aspects in this migration: end-users migration (plus product profiles) and technical users migration (used in APIs in your custom code).

If all your users (Campaign operators) are on IMS, you will still need to contact your Adobe Representative/Customer Support to plan Product Profiles Migration. You will also need to migrate Technical users you might have used in custom code. Learn more in [this page](ims-migration.md).

## Useful links {#ims-useful-links}

* [Migration of technical users to Adobe Developer console](ims-migration.md)
* [Adobe Campaign v8 release notes](../../rn/using/latest-release.md)
* [What is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
