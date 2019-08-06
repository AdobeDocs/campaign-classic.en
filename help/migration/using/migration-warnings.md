---
title: Migration warnings
seo-title: Migration warnings
description: Migration warnings
seo-description: 
page-status-flag: never-activated
uuid: 0d946090-6a02-4878-ac38-26e87b77a5dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 304e9e24-8aae-4fb9-8be2-f7dc4c95096c
index: y
internal: n
snippet: y
---

# Migration warnings{#migration-warnings}

* The migration process is reserved for expert users. You must be assisted by at least a database expert, a system administrator and an application developer from Adobe Campaign.
* Before starting migration, check that the systems and system components that you use are in fact compatible with v7. Consult the [compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).
* If you use Adobe Campaign Cloud Messaging (previously mid-sourcing), contact Adobe Campaign before beginning the entire migration procedure.
* Before starting a migration process, you **must** back up your data.
* The migration process may take several days to be completed.
* Adobe Campaign v7 is stricter than the 5.11 and 6.02 versions in terms of in configuration. This is principally to avoid problems such as data corruption and to preserve data integrity in the database. Consequently, certain functions offered in v5.11 and v6.02 may no longer work in v7 and may therefore need to be adapted after migration. Before putting into production anything, we suggest you systematically test all configurations, particularly workflows which are necessary to using Adobe Campaign.

>[!NOTE]
>
>You must also consult the [Before starting migration](../../migration/using/before-starting-migration.md) section.

