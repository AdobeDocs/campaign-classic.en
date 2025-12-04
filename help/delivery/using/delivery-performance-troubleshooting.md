---
product: campaign
title: Delivery performance and troubleshooting
description: Learn how to optimize delivery performance and troubleshoot issues in Campaign Classic v7
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
---
# Delivery performance and troubleshooting {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Comprehensive guidance on delivery performance and best practices is documented in the [Campaign v8 Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices) page. This content applies to both Campaign Classic v7 and Campaign v8 users.
>
>This page documents **Campaign Classic v7-specific configurations** for performance optimization and troubleshooting in hybrid and on-premise deployments.

For comprehensive best practices on delivery performance, platform optimization, quarantine management, database maintenance, and scheduling recommendations, refer to the [Campaign v8 Delivery best practices documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Performance optimization {#performance-optimization}

For **Campaign Classic v7 hybrid/on-premise deployments**, the following database and infrastructure optimizations can improve delivery performance.

### Database optimization

**Index addresses** to optimize the performance of SQL queries used in the application. An index can be declared from the main element of the data schema. This optimization requires direct database access and schema customization available in on-premise deployments.

### Infrastructure tuning

**Large deliveries configuration**: Deliveries to over one million recipients need space in the sending queues. For on-premise installations, MTA children can be configured to handle custom batch sizes. Contact your system administrator to adjust these settings based on your infrastructure capacity.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, infrastructure optimization and MTA configuration are managed by Adobe. Refer to the [Campaign v8 Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} for performance recommendations applicable to your deployment.

### Database maintenance {#database-maintenance}

For **Campaign Classic v7 hybrid/on-premise deployments**, platform and database maintenance directly affects delivery sending performance.

Regular maintenance tasks include:

**Database cleanup**: Use the database cleanup workflow to remove old delivery logs, tracking data, and temporary tables. Poor database maintenance can slow down delivery preparation and sending.

**Database performance monitoring**: Monitor query performance, index fragmentation, and table statistics. For detailed guidance, refer to [this page](../../production/using/database-performances.md).

**Technical workflow monitoring**: Ensure all technical workflows (especially cleanup, tracking, and deliverability update workflows) are running correctly without errors.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, database maintenance and technical workflows are monitored and managed by Adobe. Focus on delivery-specific monitoring as described in the [Campaign v8 Monitor deliveries documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Troubleshooting delivery issues {#troubleshooting}

>[!NOTE]
>
>Comprehensive guidance on delivery troubleshooting is documented in the Campaign v8 documentation, applicable to both Campaign Classic v7 and Campaign v8 users:
>
>* Common delivery failures and solutions: [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Slow delivery diagnosis: [Monitor deliveries in Campaign UI](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Delivery best practices: [Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>This section documents **Campaign Classic v7-specific troubleshooting** for hybrid and on-premise deployments.

For **Campaign Classic v7 hybrid/on-premise deployments**, the following troubleshooting steps are specific to infrastructure you manage.

### MX rules configuration

If you experience throttling issues with specific ISPs, you may need to review and adjust your MX rules configuration. For more information about MX rules and quotas, refer to [this section](../../installation/using/email-deliverability.md#about-mx-rules).

### Database maintenance for delivery performance

If you encounter the following error in mid-sourcing deployments:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

The cause is linked to performance issues where the marketing instance spends too much time building data before sending it to the mid-sourcing server.

**For on-premise installations**, perform a vacuum and reindex on the database. For more information on database maintenance, refer to [this section](../../production/using/recommendations.md).

You should also restart all workflows with a scheduled activity, and all workflows in failed status. Refer to [this section](../../workflow/using/scheduler.md).

### Technical workflow monitoring

For on-premise installations, ensure that all technical workflows related to deliverability are running without errors:

**Deliverability update workflow**: Updates bounce mail qualification rules and deliverability indicators.

**Tracking workflow**: Processes tracking data for sent deliveries.

**Database cleanup workflow**: Regularly purges old delivery logs and temporary tables to maintain performance.

Check workflow status in **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, technical workflows and infrastructure monitoring are managed by Adobe. Focus on delivery content and targeting as described in the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Related topics

* [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8 documentation)
* [Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Campaign v8 documentation)
* [Monitor deliveries in Campaign UI](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Campaign v8 documentation)
* [Database maintenance](../../production/using/recommendations.md) (v7 hybrid/on-premise)
* [Email deliverability](../../installation/using/email-deliverability.md) (v7 hybrid/on-premise)
* [Database performances](../../production/using/database-performances.md) (v7 hybrid/on-premise)

