---
product: campaign
title: Tracking logs issues
description: Tracking logs issues
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
---
# Tracking logs issues{#tracking-logs-issues}



There can be multiple reasons for tracking logs not being forwarded. We recommend that you check the following information:

* **Does the **Tracking** workflow have errors?**

Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html){target="_blank"}.

  ![](assets/tracking_scheduled_task.png)

* **Is the module **trackinglogd** running on the server?**

  Refer to [Log files](../../production/using/log-files.md).

* **Have changes been made?**

  They can trigger a loss of connection to the servers using the tracking alias.
