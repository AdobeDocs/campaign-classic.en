---
title: Restoring v6.02
seo-title: Restoring v6.02
description: Restoring v6.02
seo-description: 
page-status-flag: never-activated
uuid: 100f4af5-24ed-4aa2-be43-2f62133d0de2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: c8891bce-474f-499e-a471-0a9c34df7308
index: y
internal: n
snippet: y
---

# Restoring v6.02{#restoring-v}

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

