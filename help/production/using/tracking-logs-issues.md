---
title: Tracking logs issues
seo-title: Tracking logs issues
description: Tracking logs issues
seo-description: 
page-status-flag: never-activated
uuid: d3a2501c-6c02-47fc-8010-18174d34da5e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 3a6096db-1ea7-4587-bfed-d770a6f10cd6
index: y
internal: n
snippet: y
---

# Tracking logs issues{#tracking-logs-issues}

There can be multiple reasons for tracking logs not being forwarded. We recommend that you check the following information:

* Does the **Tracking** workflow have errors?

  Refer to [Monitoring technical workflows](../../workflow/using/executing-a-workflow.md#monitoring-technical-workflows).

  ![](assets/tracking_scheduled_task.png)

* Is the module **trackinglogd** running on the server?

  Refer to [Log files](../../production/using/log-files.md).

* Have changes been made? They can trigger a loss of connection to the servers using the tracking alias.

