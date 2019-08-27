---
title: Restoring v6.1
seo-title: Restoring v6.1
description: Restoring v6.1
seo-description: 
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
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

