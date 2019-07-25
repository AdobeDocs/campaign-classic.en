---
title: Database performances
seo-title: Database performances
description: Database performances
seo-description: 
page-status-flag: never-activated
uuid: e605a9e4-e548-4230-8d75-6a518d662681
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 5ee24805-06c7-42d6-88bc-5d71c22efcce
index: y
internal: n
snippet: y
---

# Database performances{#database-performances}

Most performance issues are linked to database maintenance. Here are four main leads to help you find the cause of slow performance:

* Configuration,
* Installation and configuration of the Adobe Campaign platform,
* Database maintenance,
* Real-time diagnosis.

## Configuration {#configuration}

Check that the initial Adobe Campaign platform configuration is still valid and if necessary, reassess your customer's needs in terms of deliverability or database size. We also recommend running a full hardware check (CPU, RAM, IO system).

>[!NOTE]
>
>You can refer to [Adobe Campaign Harware Sizing guide](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html) for insights.

## Platform configuration {#platform-configuration}

Inappropriate configuration may affect platform performance. We recommend that you check network configuration, platform deliverability options as well as MTA configuration in the **serverConf.xml** file.

## Database maintenance {#database-maintenance}

**Database cleanup task**

Please make sure the database cleanup task is operational. To do this, view the log files to see if they contain any errors. For more on this, refer to [this section](../../production/using/database-cleanup-workflow.md).

**Maintenance plans**

Make sure database maintenance is correctly scheduled and executed. To do this, please contact your database administrator to learn more about:

* their maintenance schedule,
* previously executed maintenance plans,
* view the script logs.

For more on this, refer to [this section](../../production/using/recommendations.md).

>[!CAUTION]
>
>If you are using a mid-sourcing configuration, it is essential for databases to be maintained on a regular basis. When analyzing a delivery on the marketing platform, the marketing instance sends information to the mid-sourcing instance. If the process is slowed down, the marketing instance will be impacted.

**Managing work tables**

Please check the number and size of work tables. When they exceed a certain size, database performance is affected. These tables are created by workflows and deliveries. They remain in the database while workflows and deliveries are active. To limit the size of work tables, you can carry out the following operations:

* stop or delete deliveries with the following statuses: **Failed**, **In progress**, **Ready for delivery**, or **Paused**. 
* stop or delete workflows which are paused due to an error,
* stop all workflows used for tests which do not contain an **End** activity and whose status therefore remains **Paused**.

>[!CAUTION]
>
>If the operation takes a long time and frees up a lot of space, this means that in-depth maintenance is necessary (index rebuilding, etc.). For more on this, refer to [this section](../../production/using/recommendations.md).

**Adobe Campaign process monitoring**

Depending on Adobe Campaign installation settings, two tools can be used for platform monitoring:

* the instance production page. For more on this, refer to [Manual monitoring](../../production/using/database-performances.md#manual-monitoring). 
* the netreport script. For more on this, refer to [Automatic monitoring via Adobe Campaign scripts](../../production/using/database-performances.md#automatic-monitoring-via-adobe-campaign-scripts).

## Specifics {#specifics}

It may become necessary to run a real-time diagnosis to identify the cause of the issue. Start by checking the process and platform log files, then monitor database activity while recreating the issue. Pay particular attention to the following:

* the maintenance execution plan,
* SQL queries being executed,
* whether or not external processes are running at the same time (cleansing, imports, aggregate calculation, etc.).

