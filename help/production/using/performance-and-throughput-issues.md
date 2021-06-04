---
product: campaign
title: Performance and throughput issues
description: Performance and throughput issues
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
---
# Performance and throughput issues{#performance-and-throughput-issues}

First of all, you should check that you have the latest build installed. This ensures that you have the latest features and bug fixes.

Refer to the [Release Notes](../../rn/using/latest-release.md) for more information on the content of each release.

## Hardware and infrastructure {#hardware-and-infrastructure}

General guidelines for hardware requirements for on-premise Campaign Classic are detailed on this [page](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html).

The consulting team can provide hosted customers with a tool that allows you to easily view how much space is used by various types of tables in the database as well as the space used on the SFTP site. It additionally provides tools to allow you to clean up unnecessary data. Contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) if you need this tool implemented. Here are a few important things to check using this tool:

* If index size is larger than table size, then a vacuum is required.
* Check the tables which have the maximum bloat. If these tables are frequently used, they need to be vacuumed. 
* Database blocking can cause emails to stop being sent.

Adobe Campaign also provides a [tool](../../production/using/monitoring-processes.md#manual-monitoring) to check CPU and RAM usage. Use this tool and look at specific indicators such as: **Memory**, **Swap Memory**, **Disk**, **Active Processes**. If the values are too high, you can try reducing the number of workflows or schedule workflows to start at different times.

## Database check {#database-performances}

Most of the time, performance issues are linked to database maintenance. Here are the main items to check:

* Configuration: we recommend checking the initial Adobe Campaign platform configuration and running a full hardware check. 
* Installation and configuration of the Adobe Campaign platform: check network configuration and platform deliverability options.
* Database maintenance: make sure that the database cleanup task is operational and that the database maintenance is correctly scheduled and executed. Check the number and size of work tables. 
* Real-time diagnosis: check the process and platform log files, then monitor database activity while recreating the issue.

>[!NOTE]
>
>For more information, refer to this section: [Database performance](../../production/using/database-performances.md).

## Application configuration {#application-configuration}

Here are is a list of articles related to application configuration best practices:

* MTA and MTAChild processes and memory: the **mta** module distributes messages to its **mtachild** child modules. Each **mtachild** prepares messages before requesting an authorization from the statistics server, and sending them. Refer to this [page](../../installation/using/email-deliverability.md) for more information.
* TLS configuration: enabling TLS globally is not recommended because it can reduce throughput. Instead, per-domain TLS settings, managed by deliverability team, should be tuned depending on the needs. Refer to this [page](../../installation/using/email-deliverability.md#mx-configuration) for more information. 
* DKIM: to insure the security level of the DKIM, 1024b is the best practice recommended encryption size. Lower DKIM keys will not be considered as valid by the majority of access providers. Refer to [this page](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

## Deliverability issues {#deliverability-issues}

Here are is a list of best practices and articles related to deliverability:

* IP reputation: if the IP reputation is not good enough, there will be an impact on performance. The **Deliverability Monitoring** module offers various tools to track the deliverability performance of your platform. Refer to this [page](../../delivery/using/monitoring-deliverability.md). 
* IP warm-up: the IP warm-up is performed by the deliverability team. This involves gradually increasing the number of emails through new IPs over a period of a few weeks.
* IP affinity setup: an incorrect IP affinity setup can stop the emails altogether (incorrect operator/affinity name in configuration) or reduce the throughput (small number of IPs in the affinity). Refer to this [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Email size: email size plays an important role in throughput. The recommended maximum email size is 60 KB. Refer to this [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html). In the [Delivery throughput](../../reporting/using/global-reports.md#delivery-throughput) report, check the number of bytes transferred by hour. 
* Large number of invalid recipients: when there is a large number of invalid recipients, it can impact throughput. The MTA keeps retrying sending emails to invalid recipients. Please make sure your database is well maintained.
* Amount of personalization: if a delivery stays in "Personalization in progress", check the JavaScript used in personalization blocks.

>[!NOTE]
>
>See also the [Deliverability](../../delivery/using/about-deliverability.md) section. For a deeper dive on deliverability, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).
