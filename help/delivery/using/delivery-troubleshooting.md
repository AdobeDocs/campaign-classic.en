---
product: campaign
title: Delivery sending troubleshooting
description: Learn more about delivery performances and how to troubleshoot issues related to delivery monitoring
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
---
# Delivery sending troubleshooting {#delivery-troubleshooting}

>[!NOTE]
>
>Comprehensive guidance on delivery troubleshooting is documented in the Campaign v8 documentation, applicable to both Campaign Classic v7 and Campaign v8 users:
>
>* Common delivery failures and solutions: [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Slow delivery diagnosis: [Monitor deliveries in Campaign UI](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Delivery best practices: [Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>This page documents **Campaign Classic v7-specific troubleshooting** for on-premise deployments.

## Campaign Classic v7-specific troubleshooting {#v7-specific}

For **Campaign Classic v7 on-premise installations**, the following troubleshooting steps are specific to infrastructure you manage:

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
* [Database maintenance](../../production/using/recommendations.md) (v7 on-premise)
* [Email deliverability](../../installation/using/email-deliverability.md) (v7 on-premise)
