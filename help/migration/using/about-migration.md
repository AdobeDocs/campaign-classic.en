---
product: campaign
title: Migration to Campaign Classic
description: Learn how to migrate to Campaign Classic from a previous Campaign version
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
---
# Get started with the migration{#about-migration}

![](../../assets/v7-only.svg)

This document details the prerequisites to a migration, the steps for a migration to Adobe Campaign Classic v7. Steps and optional settings depend on your configuration. 

The migration process must be carried out with caution, its impacts must be fully considered beforehand and the procedure must be carried out rigorously. It must only be performed by an expert user. We strongly recommend getting in touch with [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) before starting any migration procedure.

The migration must be tested on the test/stage environment beforehand to make sure it runs smoothly and without any errors. Migrating the production environment must only be performed once the migrated test environment is fully validated.

>[!NOTE]
>
>New features and improvements coming with Adobe Campaign v7 are detailed in the [Release Notes](../../rn/using/latest-release.md).


## Prerequisites

* The migration process must be performed by expert users. You must be assisted by at least a database expert, a system administrator and an application developer from Adobe Campaign.
* Before starting migration, check that the systems and system components that you use are compatible with v7. [Learn more](../../rn/using/compatibility-matrix.md).
* If you use Adobe Campaign Cloud Messaging (mid-sourcing deployment), contact Adobe Customer Care before starting.
* Before starting a migration process, you **must** back up your data.
* The migration process may take several days to be completed.
* Adobe Campaign v7 is a more secure version than the previous ones: this impacts configuration guidelines to avoid problems such as data corruption and to preserve data integrity in the database. As a customer, you are respoonsible for testing all configurations, including workflows.

More prerequisites are available in [this page](../../migration/using/before-starting-migration.md).


## Modernized environment {#modernizing-your-environment}

Performing a migration can be a chance to update your environment (database engines, operating systems). Adobe Campaign strongly recommends upgrading your production environments to the most recent versions.

>[!CAUTION]
>
>For further information about the versions supported by Adobe Campaign v7, refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md).

## Key migration steps {#key-migration-steps}

The general procedure for migrating to Adobe Campaign v7 is detailed in [this page](../../migration/using/before-starting-migration.md).


## Specific configurations {#specific-configurations}

The changes brought about by Adobe Campaign v7 may also mean that you have to adapt certain specific configurations developed in the earlier versions. Therefore, it may be necessary to perform an audit on all your configurations before the migration: contact Adobe Campaign for any assistance.

For example, particular attention should be paid to specific settings for Web applications, schema extensions with SQLdata or out-of-the-box schema cloning. For more information, refer to [this page](../../migration/using/configuring-your-platform.md).

Similarly, in order to respond to the heightened security within Adobe Campaign, some internal mechanisms have been modified: you must adapt these configurations accordingly.

