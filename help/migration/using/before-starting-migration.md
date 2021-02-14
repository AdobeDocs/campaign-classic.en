---
solution: Campaign Classic
product: campaign
title: Before starting migration
description: Before starting migration
audience: migration
content-type: reference
topic-tags: migration-procedure
---

# Prerequisites {#before-starting-migration}

>[!NOTE]
>
>In this document, commands linked to the database are given as an example. These may vary depending on their configuration. Contact your database administrator.

## Recommendations{#migration-recommentations}

As the migration procedure is sensitive, we strongly recommend reading this document thoroughly before starting the procedure.

* The migration process must be performed by expert users only. You must be assisted at least by a database expert, a system administrator and an application developer from Adobe Campaign.
* Before starting migration, check that the systems and system components that you use are in fact compatible with v7. Consult the [compatibility matrix](../../rn/using/compatibility-matrix.md).
* If you use Adobe Campaign Cloud Messaging (mid-sourcing), contact Adobe before beginning the migration procedure.
* Before starting a migration process, you **must** back up your data.
* The migration process may take several days to be completed.
* To avoid data corruption and preserve data integrity in the database, Adobe Campaign v7 is stricter than the 5.11 and 6.02 versions in terms of in configuration. As a consequence, certain functions available in v5.11 and v6.02 may no longer work in v7 and may need to be adapted after migration. You need to **test all configurations** before moving to production.

## Initial steps{#installed-version}

Before starting the migration, you must:

1. Install the latest build
    Before migrating, you must install the latest build of the current version that you are using.
    
    Check the version on your server by going to the **[!UICONTROL Help > About]** menu on the client console or using the **nlserver pdump** command.

1. Backup your data
    Before starting a migration process, you **must** back up your data.

>[!IMPORTANT]
>
>   * You cannot change your database engine type (DBMS), but you can upgrade its version.
>   * It is not possible to move from a non-Unicode database to a Unicode database.

## Migration steps{#migration-steps}

The migration procedure must be carried out on **all** servers and in a specific sequence.

* In the case of a [Standalone Deployment](../../installation/using/standalone-deployment.md) (single machine mode), the application is migrated in one step.
* In the case of an [Enterprise Deployment](../../installation/using/enterprise-deployment.md), migration steps are:

    1. Migrate the marketing server. 
    1. Migrate the mail server (mta).
    1. Migrate the redirection and tracking servers (Apache / IIS).

* In the case of a **Cloud Messaging platform**, the execution servers are hosted at Adobe Campaign. Please contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). to coordinate migration between different servers.
* In the case of a [Power Booster or Power Cluster platform](../../installation/using/power-booster-and)power-cluster.md), migration steps are:

    1. Migrate the redirection and tracking servers (Apache / IIS).
    1. Migrate the Power Booster/Cluster servers.
    1. Migrate the marketing server.

## Secure passwords {#user-passwords}

In v7, **internal** and **admin** operator connection must be secured by a password. We strongly recommend assigning passwords to these accounts and all operator accounts, **before migration**. If you have not specified a password for **internal**, you will not be able to connect. To assign a password to **internal**, enter the following command:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>The **internal** password must be identical for all the tracking servers. For more information, refer to the [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier) and [About permissions](../../platform/using/access-management.md#about-permissions) sections.

