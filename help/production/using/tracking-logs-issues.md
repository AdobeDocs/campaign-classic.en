---
solution: Campaign Classic
product: campaign
title: Tracking logs issues
description: Tracking logs issues
audience: production
content-type: reference
topic-tags: troubleshooting
---

# Tracking logs issues{#tracking-logs-issues}

There can be multiple reasons for tracking logs not being forwarded. We recommend that you check the following information:

* **Does the **Tracking** workflow have errors?**

  Refer to [Monitoring technical workflows](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **Is the module **trackinglogd** running on the server?**

  Refer to [Log files](../../production/using/log-files.md).

* **Have changes been made?**

  They can trigger a loss of connection to the servers using the tracking alias.
