---
solution: Campaign Classic
product: campaign
title: Migration method
description: Migration method
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
---
# Migration method{#migration-method}

## Modernizing your environment {#modernizing-your-environment}

Performing a migration can be a chance to update your environment (database engines, operating systems). Adobe Campaign strongly recommends upgrading your production environments to the most recent versions.

32-bit version databases and operating systems are still supported in v7, but will no longer be supported in future versions of Adobe Campaign. We strongly recommend you upgrade your platform to 64 bits as soon as possible.

In v6.02, the "multi timezone" mode was only available for PostgreSQL database engines. It is now offered no matter what type of database engine is used. We strongly recommend that you transform your base to a "multi timezone" base. For more information on this, see the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

>[!IMPORTANT]
>
>Some software versions supported in Adobe Campaign 5.11 and 6.02 are no longer supported in Adobe Campaign v7.
>
>For further information about the versions supported by Adobe Campaign, consult the [compatibility matrix](../../rn/using/compatibility-matrix.md).

## Key migration steps {#key-migration-steps}

The general procedure for migrating to Adobe Campaign v7 is detailed in the [Before starting migration](../../migration/using/before-starting-migration.md) section.

Implementation steps for the migration to Adobe Campaign v7 are detailed in the [Prerequisites for migration to Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) section.

The required configurations depend on your existing configurations and the initial version of the platform. These are outlined in the [General configurations](../../migration/using/general-configurations.md) section.

## Specific configurations {#specific-configurations}

The changes brought about by Adobe Campaign v7 may also mean that you have to adapt certain specific configurations developed in the earlier versions. Therefore, it may be necessary to perform an audit on all your configurations before the migration: contact Adobe Campaign for any assistance.

For example, particular attention should be paid to specific settings for Web applications, schema extensions with SQLdata or out-of-the-box schema cloning. For more information, refer to the [Configuring your platform](../../migration/using/configuring-your-platform.md) section.

Similarly, in order to respond to the heightened security within Adobe Campaign, some internal mechanisms have been modified: you must adapt these corresponding configurations.
