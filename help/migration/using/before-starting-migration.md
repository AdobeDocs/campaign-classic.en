---
product: campaign
title: Before starting migration
description: Before starting migration
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
---
# Before starting migration{#before-starting-migration}

>[!NOTE]
>
>In this document, commands linked to the database are given as an example. These may vary depending on their configuration. Contact your database administrator.

## Warnings {#warnings}

* The migration process must be performed only by expert users. You must be assisted by at least a database expert, a system administrator and an application developer from Adobe Campaign.
* Before starting migration, check that the systems and system components that you use are in fact compatible with v7. Consult the [compatibility matrix](../../rn/using/compatibility-matrix.md).
* If you use Adobe Campaign Cloud Messaging (mid-sourcing), contact Adobe before beginning the entire migration procedure.
* Before starting a migration process, you **must** back up your data.
* The migration process may take several days to be completed.
* Adobe Campaign v7 is stricter than the 5.11 and 6.02 versions in terms of in configuration. This is principally to avoid problems such as data corruption and to preserve data integrity in the database. Consequently, certain functions offered in v5.11 and v6.02 may no longer work in v7 and may therefore need to be adapted after migration. Before putting into production anything, we suggest you systematically test all configurations, particularly workflows which are necessary to using Adobe Campaign.

### Installed version {#installed-version}

Before migrating, you should install the latest build of the current version that you are using.

Check the version on your server by going to the **[!UICONTROL Help> About]** menu on the client console using the **nlserver pdump** command.

### Data backup {#data-backup}

Before starting a migration process, you **must** back up your data.

### Environment {#environment}

* It is not possible to change your database engine type (DBMS). For instance, you cannot switch from a PostgreSQL engine to an Oracle engine. However, you can switch from an Oracle 8 engine to an Oracle 10 engine.
* It is not possible to go from a non-Unicode database to a Unicode database.

### Recommendation {#recommendation}

As the migration procedure is sensitive, we strongly recommend reading this document thoroughly before starting the procedure.

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

## User passwords {#user-passwords}

In v7, **internal** and **admin** operator connection must be secured by a password. We strongly recommend assigning passwords to these accounts and all operator accounts, **before migration**. If you have not specified a password for **internal**, you will not be able to connect. To assign a password to **internal**, enter the following command:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>The **internal** password must be identical for all the tracking servers. For more information, refer to the [Internal identifier](../../installation/using/configuring-campaign-server.md#internal-identifier) and [Permissions](../../platform/using/access-management.md) sections.
