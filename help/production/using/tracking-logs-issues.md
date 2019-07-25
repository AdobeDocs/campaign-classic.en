---
title: Tracking logs issues
seo-title: Tracking logs issues
description: Tracking logs issues
seo-description: 
page-status-flag: never-activated
uuid: 71214d01-dce8-41d3-aa94-5670ce44c295
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 32a700c1-0a55-4b38-9a1e-c6fb0209d12b
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

