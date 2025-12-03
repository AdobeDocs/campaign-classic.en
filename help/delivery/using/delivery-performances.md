---
product: campaign
title: Delivery performances best practices
description: Learn more about delivery performances and best practices
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
---
# Delivery performances best practices {#delivery-performances}

>[!NOTE]
>
>Comprehensive guidance on delivery performance and best practices is documented in the [Campaign v8 Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices) page. This content applies to both Campaign Classic v7 and Campaign v8 users.
>
>This page documents **Campaign Classic v7-specific performance configurations** for on-premise deployments.

For comprehensive best practices on delivery performance, platform optimization, quarantine management, database maintenance, and scheduling recommendations, refer to the [Campaign v8 Delivery best practices documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Campaign Classic v7-specific performance tuning {#best-practices-performance}

For **Campaign Classic v7 on-premise installations**, the following database and infrastructure optimizations can improve delivery performance:

### Database optimization

**Index addresses** to optimize the performance of SQL queries used in the application. An index can be declared from the main element of the data schema. This optimization requires direct database access and schema customization available in on-premise deployments.

### Infrastructure tuning

**Large deliveries configuration**: Deliveries to over one million recipients need space in the sending queues. For on-premise installations, MTA children can be configured to handle custom batch sizes. Contact your system administrator to adjust these settings based on your infrastructure capacity.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, infrastructure optimization and MTA configuration are managed by Adobe. Refer to the [Campaign v8 Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} for performance recommendations applicable to your deployment.

## Campaign Classic v7 database maintenance {#performance-issues}

For **Campaign Classic v7 on-premise installations**, platform and database maintenance directly affects delivery sending performance.

Regular maintenance tasks include:

**Database cleanup**: Use the database cleanup workflow to remove old delivery logs, tracking data, and temporary tables. Poor database maintenance can slow down delivery preparation and sending.

**Database performance monitoring**: Monitor query performance, index fragmentation, and table statistics. For detailed guidance, refer to [this page](../../production/using/database-performances.md).

**Technical workflow monitoring**: Ensure all technical workflows (especially cleanup, tracking, and deliverability update workflows) are running correctly without errors.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, database maintenance and technical workflows are monitored and managed by Adobe. Focus on delivery-specific monitoring as described in the [Campaign v8 Monitor deliveries documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Related topics

* [Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Campaign v8 documentation)
* [Monitor your deliverability](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (Campaign v8 documentation)
* [Delivery troubleshooting](delivery-troubleshooting.md)
* [Database performances](../../production/using/database-performances.md) (v7 on-premise)
