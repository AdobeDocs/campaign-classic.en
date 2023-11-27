---
title: Migrate Campaign operators to Adobe Identity Management System (IMS)
description: Learn how to migrate Campaign operators to Adobe Identity Management System (IMS)
exl-id: 58c130d8-8ba8-42ce-9ab4-a697125d3f85
---
# Migrate Campaign operators to Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Starting Campaign v8.6, the authentication process to Campaign v8 is being improved. All operators will use [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} **only** to connect to Campaign. Connecting with user/password (aka native authentication) will no longer be allowed. Adobe recommends to perform this migration in Campaign v8.5.2 to be able to migrate smoothly to Campaign v8.6.

As a Campaign Classic v7 managed services customer, if you are migrating to Campaign v8, this procedure also applies to you.

This article details the steps required to migrate a technical operator to technical account on Adobe Developer console.

## What changed?{#move-to-ims-changes}

With Campaign v8, all regular users should already connect to the Adobe Campaign client console using their Adobe ID, through Adobe Identity Management System (IMS). However, with some older configurations, user/password connections were still available. **This will no longer be permitted starting Campaign v8.6.**

In addition, as part of the effort to reinforce security and authentication process, Adobe Campaign client application now calls Campaign APIs directly using the IMS technical account token. Migration for technical operators is detailed in a dedicated article, available in [this page](ims-migration.md).

This change is applicable starting Campaign v8.5.2, and will be **mandatory** starting Campaign v8.6. 

## Are you impacted?{#migrate-ims-impacts}

If operators in your organization are connecting to Campaign client console using their login/password (aka. native authentication), you are impacted, and must migrate these operator(s) to Adobe IMS as detailed below.

Migration to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is a security imperative to make your environments secure and standardized, as most of the other Adobe Experience Cloud solutions and apps are already on IMS.

## How to migrate?{#ims-migration-procedure}

### Prerequisites{#ims-migration-prerequisites}

Before starting the migration process, you must reach out to your Adobe representative (Transition Manager) so that Adobe technical teams can migrate your existing Operator groups and Named rights to Adobe Identity Management System (IMS).

### Key steps {#ims-migration-steps}

Key steps for this migration are listed below: 

1. Adobe upgrades your environments to Campaign v8.5.2.
1. After the upgrade, you can still create new users with both methods, as native user or with IMS.
1. Your internal Campaign Administrator must add unique emails to all native users on the Campaign client console, and confirm to your Adobe Transition Manager once this is done. This step is detailed in [this section](#ims-migration-id).
1. Work with Adobe to secure a date for Adobe to run automated migration for your non-technical users (operators) and product profiles. This step requires an hour window with no downtime to any of your instances.
1. Your internal Campaign Administrator validates these changes, and provides sign-off. After this migration, you must no longer create any further operator authenticating with his login and password.

You can now migrate your technical operator(s) to Adobe Developer Console as detailed in [this technote](ims-migration.md). This step is mandatory if you are using Campaign APIs.

Once this migration is completed, confirm to your Adobe Transition Manager: Adobe then marks the migration as complete, and blocks new native user creation and native user login. Your environment is then secured and standardized. 

## Frequently Asked Questions {#ims-migration-faq}

### When can I start the migration? {#ims-migration-start}

A prerequisite for the migration to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is to upgrade your environment to Campaign v8.5.2.

You can start IMS migration on your stage environment, once it is upgraded to Campaign v8.5.2, and accordingly plan for production environment.

### What happens after build upgrade to Campaign v8.5.2? {#ims-migration-after-upgrade}

After your environments have been upgraded to Campaign v8.5.2, you can initiate your transition to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}. 

New native user creation is still allowed until the IMS migration is complete. 

### When is the migration complete? {#ims-migration-end}

Once end-user migration and technical user migration to Adobe Identity Management System (IMS) is done, you must contact your Adobe Transition Manager so that Adobe can mark your migration as complete, and block user creation from the client console, and disable native user login.


### How to create users after migration? {#ims-migration-native}

Once full IMS migration is complete, Adobe will apply the restrictions which will block new native user creation. These restrictions are not applied until IMS migration is complete.

For new customers - new native user creation is not permitted from the beginning.

As a Campaign Administrator, you can grant permissions to the users of your organization through Adobe Admin Console and Campaign Client Console. Users log on to Adobe Campaign with their Adobe ID. Learn more in [this documentation](../../v8/start/gs-permissions.md).

### How to add emails for current native users? {#ims-migration-id}

As a Campaign Administrator, you must add email IDs to all native users from the client console. To perform this, follow the steps below:

1. Connect to the client console and browse to **Administration > Access Management > Operators**.
1. Select the operator to update in the operator list.
1. Enter the email of the operator in the **Contact points** section of the operator form.
1. Save your changes.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### How to log in to Campaign via IMS? {#ims-migration-log}

Learn how to connect to Campaign with your Adobe ID in [this section](../../v8/start/connect.md).

### Will there be a downtime during this migration? {#ims-migration-downtime}

To finalize the migration (migrate users and product profiles), Adobe requires one hour window with no downtime to any of your instances (workflows, etc).

During this timeframe, all Campaign users need to log off, and log back with their Adobe ID once the migration to IMS is finalized.

### What happens to users that are logged in during IMS user migration? {#ims-migration-log-off}

Adobe strongly recommends all users should be logged off during the migration window.

### Users in my organization are already using IMS, do I still need to perform IMS Migration?{#ims-migration-needed}

There are 2 aspects in this migration: end-users migration and technical users migration (used in APIs in your custom code).

If all your users (Campaign operators) are on IMS you do not need to perform this migration. However, you still need to migrate Technical users you might have used in custom code. Learn more in [this page](ims-migration.md).

Once this migration is done, you must contact your Adobe Transition Manager so that Adobe finalizes the migration.

## Useful links {#ims-useful-links}

* [Migration of technical users to Adobe Developer console](ims-migration.md)
* [How to connect to Adobe Campaign v8](../../v8/start/connect.md)
* [Access and permissions in Adobe Campaign v8](../../v8/start/gs-permissions.md)
* [Adobe Campaign v8 release notes](../../v8/start/release-notes.md)
* [What is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
