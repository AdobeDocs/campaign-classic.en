---
title: Before starting migration
seo-title: Before starting migration
description: Before starting migration
seo-description: 
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
index: y
internal: n
snippet: y
---

# Before starting migration{#before-starting-migration}

>[!NOTE]
>
>In this document, commands linked to the database are given as an example. These may vary depending on their configuration. Contact your database administrator.

## Warnings {#warnings}

### Installed version {#installed-version}

Before migrating, you should install the latest build of the current version that you are using.

Check the version on your server by going to the **[!UICONTROL Help> About]** menu on the client console using the **nlserver pdump** command.

### Data backup {#data-backup}

Before starting a migration process, you **must** back up your data.

### Environment {#environment}

* It is not possible to change your database engine type (DBMS). For instance, you cannot switch from a PostgreSQL engine to an Oracle engine. However, you can switch from an Oracle 8 engine to an Oracle 10 engine.
* It is not possible to go from a non-Unicode database to a Unicode database.

### Recommendation {#recommendation}

As the migration procedure is particularly sensitive, we strongly recommend reading this document thoroughly before starting the procedure.

## Migration steps {#migration-steps}

The migration procedure must be carried out on **all** servers and in a particular order.

* In the case of a **standalone platform** (single machine mode), the application is migrated in its entirety.
* In the case of a **standard platform** (enterprise), the migration steps are as follows:

    1. Migrate the marketing server. 
    1. Migrate the mail server (mta).
    1. Migrate the redirection and tracking servers (Apache / IIS).

* In the case of a **Cloud Messaging platform**, the execution servers are hosted at Adobe Campaign. Please contact Adobe Campaign to coordinate migration between different servers.
* In the case of a **Power Booster or Power Cluster platform**, the migration steps are as follows:

    1. Migrate the redirection and tracking servers (Apache / IIS).
    1. Migrate the Power Booster/Cluster servers.
    1. Migrate the marketing server.

>[!NOTE]
>
>Communication between a v6.02 marketing server and a v7 Cloud Messaging or Power Booster/Cluster server is possible. Nevertheless, if you decide to keep your v6.02 marketing server, this must be updated with the most recent v6.02 build before migrating to the Cloud Messaging or Power Booster/Cluster.

## User passwords {#user-passwords}

In v7, **internal** and **admin** operator connection must be secured by a password. We strongly recommend assigning passwords to these accounts and all operator accounts, **before migration**. If you have not specified a password for **internal**, you will not be able to connect. To assign a password to **internal**, enter the following command:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>The **internal** password must be identical for all the tracking servers. For more information, refer to the [Internal identifier](../../installation/using/configuring-campaign-server.md#internal-identifier) and [About permissions](../../platform/using/access-management.md#about-permissions) sections.

