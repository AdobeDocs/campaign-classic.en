---
solution: Campaign Classic
product: campaign
title: Rollback to the previous version
description: Learn how to rollback to the previous version
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
---
# Rollback to the previous version{#about-rollback}

After a migration, in case of issues, you might need to rollback to the previous version of Campaign.

The rollback procedure depends on your initial version of Campaign.

## Restoring v6.1

Here is the procedure to restore a v6.1 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Adobe Campaign v6.back** folder (**nl6.back** in Linux), rename it to **Adobe Campaign v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.1 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.1 service.

## Restoring to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restoring to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.
