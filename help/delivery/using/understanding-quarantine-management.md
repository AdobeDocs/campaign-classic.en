---
product: campaign
title: Understand quarantine management
description: Understand quarantine management
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
---
# Understand quarantine management{#understanding-quarantine-management}

>[!NOTE]
>
>Comprehensive guidance on quarantine management is documented in the [Campaign v8 Quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines) page. This content applies to both Campaign Classic v7 and Campaign v8 users, covering:
>
>* Quarantine vs denylist concepts
>* Why addresses are sent to quarantine (hard/soft errors)
>* Soft error management and error counter thresholds
>* How to access and identify quarantined addresses
>* How to remove addresses from quarantine (automatic, manual, bulk)
>* Quarantine management reports
>
>This page documents **Campaign Classic v7-specific configuration** for quarantine management in hybrid and on-premise deployments.

For comprehensive quarantine management guidance, refer to the [Campaign v8 Quarantine management documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Quarantine configuration {#v7-quarantine-config}

The following configuration options are available for **Campaign Classic v7 hybrid/on-premise deployments** to customize quarantine behavior.

### Soft error threshold configuration {#soft-error-threshold}

For on-premise installations using the legacy Campaign MTA, you can modify the number of errors and the period between two errors before an address is quarantined.

To configure these settings:

1. Access the deployment wizard from **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**
2. Navigate to **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Configure:
   * **Number of errors**: The maximum number of soft errors before an address is quarantined (default: 5)
   * **Period between two significant errors**: The time window (in seconds) for error counting (default: 86,400 seconds = 1 day)

When the error counter reaches the threshold, the address is quarantined. If the last significant error occurred more than 10 days ago, the error counter is reinitialized.

For more details, refer to [this page](communication-channels.md) under **Delivery sending** > **Configure retries**.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, retry settings and error thresholds are managed by Adobe based on IP performance and domain reputation. No configuration is required.

### Database cleanup workflow {#database-cleanup-workflow}

For on-premise installations, the **[!UICONTROL Database cleanup]** technical workflow automatically removes quarantined addresses that match specific conditions.

Access this workflow from **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**.

The workflow removes addresses from quarantine in the following cases:

* Addresses in **[!UICONTROL With errors]** status after a successful delivery
* Addresses in **[!UICONTROL With errors]** status if the last soft bounce occurred more than 10 days ago
* Addresses in **[!UICONTROL With errors]** status with **[!UICONTROL Mailbox full]** error after 30 days

Ensure this workflow runs regularly (recommended: daily) to maintain quarantine list hygiene.

For more on database cleanup, refer to [this section](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, the database cleanup workflow is monitored and managed by Adobe.

### Push notification quarantine specifics {#push-quarantine-specifics}

For Campaign Classic v7, push notification quarantines follow the general quarantine mechanism with some channel-specific behaviors.

For **iOS** and **Android** push notifications, the quarantine mechanism uses device tokens rather than email addresses. When a mobile application is uninstalled or reinstalled, the associated token is quarantined.

For detailed information about push notification quarantine scenarios (iOS and Android error types, retry behavior, etc.), refer to the [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} documentation which includes comprehensive push notification error type tables.

### SMS quarantine specifics {#sms-quarantine-specifics}

For Campaign Classic v7, SMS quarantines follow the general quarantine mechanism with some channel-specific behaviors related to phone numbers rather than email addresses.

The SMS quarantine mechanism varies depending on the connector used:

* **Standard SMPP connectors**: Error qualification rules defined in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** apply to SMS deliveries.

* **Extended generic SMPP connector**: Error management is handled differently using regular expressions (regexes) to parse Status Report (SR) messages returned by the SMSC provider.

For detailed information about SMS quarantine scenarios and error types, refer to the [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} documentation which includes comprehensive SMS error type tables.

## Related topics

* [Quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8 documentation)
* [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8 documentation)
* [Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Campaign v8 documentation)
* [Database cleanup workflow](../../production/using/database-cleanup-workflow.md) (v7 hybrid/on-premise)
* [Configure delivery retries](communication-channels.md) (v7 hybrid/on-premise)
