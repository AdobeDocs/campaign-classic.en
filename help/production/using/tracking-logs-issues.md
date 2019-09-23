---
title: Tracking logs issues
seo-title: Tracking logs issues
description: Tracking logs issues
seo-description: 
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
index: y
internal: n
snippet: y
---

# Tracking logs issues{#tracking-logs-issues}

There can be multiple reasons for tracking logs not being forwarded. We recommend that you check the following information:

* Does the **Tracking** workflow have errors?

  Refer to [Monitoring technical workflows](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* Is the module **trackinglogd** running on the server?

  Refer to [Log files](../../production/using/log-files.md).

* Have changes been made? They can trigger a loss of connection to the servers using the tracking alias.

