---
product: campaign
title: Before starting migration
description: Before starting migration
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: yes
hidefromtoc: yes
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
---
# Prerequisites{#before-starting-migration}

![](../../assets/v7-only.svg)

This page lists specific steps to perform before starting the migration process. You must also refer to [this page](about-migration.md) for more guidance.

>[!NOTE]
>
>In this document, commands are given as samples. They can vary depending on your configuration.

1. Check your Adobe Campaign version: before migrating, install the latest build of the current version that you are using.
1. Back up your data.
1. Check your environment: you cannot change your database engine system (DBMS). For instance, you cannot switch from a PostgreSQL engine to an Oracle engine. However, you can switch to the latest versiuon of your database engine. Note that it is not possible to go from a non-Unicode database to a Unicode database.

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

>[!CAUTION]
>
>The **internal** password must be identical for all the tracking servers. For more information, refer to the [Internal identifier](../../installation/using/configuring-campaign-server.md#internal-identifier) and [Permissions](../../platform/using/access-management.md) sections.
