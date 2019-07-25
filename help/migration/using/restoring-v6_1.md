---
title: Restoring v6.1
seo-title: Restoring v6.1
description: Restoring v6.1
seo-description: 
page-status-flag: never-activated
uuid: b020fc9d-16ec-4fbe-bdac-fef98107fa77
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: da8ed576-045b-4b61-80be-e34cab3ed92e
index: y
internal: n
snippet: y
---

# Restoring v6.1{#restoring-v}

Here is the procedure to restore a v6.1 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Adobe Campaign v6.back** folder (**nl6.back** in Linux), rename it to **Adobe Campaign v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.1 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.1 service.

