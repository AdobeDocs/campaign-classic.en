---
product: campaign
title: Get started with delivery monitoring
description: Learn more about Campaign Classic delivery monitoring capabilities
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
---
# Get started with delivery monitoring {#about-delivery-monitoring}

>[!IMPORTANT]
>
>This page documents **Campaign Classic v7-specific monitoring features** for hybrid and on-premise deployments.

## Monitoring features

### Delivery monitoring {#monitoring-deliveries}

**For Campaign Classic v7 hybrid/on-premise deployments**, additional monitoring is required for server resources and MTA (Mail Transfer Agent) configuration.

#### Troubleshoot pending deliveries {#pending-deliveries}

What if the deliveries are not being sent and their status remains **Pending**?

* The execution process is waiting on the availability of some resources. The MTA may have not been started.
Check that your mta@instance modules are launched on your MTA servers and start the MTA module if necessary. [Learn more](../../production/using/administration.md).

* The delivery may be using an affinity that has not been configured on the sending instance.
Tip: Check the configuration of traffic management (IP affinity). For more on this, see Control outgoing SMTP traffic.

>[!NOTE]
>
>These steps can only be performed by an expert user on on-premise installations.

### Deliverability monitoring {#deliverability-monitoring}

#### Deliverability package installation {#deliverability-package}

This feature is available through a dedicated package in Adobe Campaign. To use it, this package must be installed. Once done, restart the server for the package to be taken into account.

* For hosted and hybrid clients, **Deliverability monitoring** is configured on your instance by Adobe technical support and consultants. For more information, contact your Adobe Account executive.
 
* For on-premise installations, you must install the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. For more on this, see [Install Campaign Classic standard packages](../../installation/using/installing-campaign-standard-packages.md).

#### Deliverability workflow {#deliverability-workflow}

In Adobe Campaign Classic, **Deliverability monitoring** is managed by the **[!UICONTROL Refresh for deliverability]** workflow. It is installed by default on all instances and lets you initialize the list of bounce mail qualification rules, the list of domains and the list of MXs. Once the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package is installed, this workflow runs nightly to regularly update the list of rules and enables you to actively manage platform deliverability.

**The Deliverability package gives you access to:**

* The [Inbox rendering report](inbox-rendering.md) which enables you to preview your messages on major email clients in order to scan content and reputation.
* Overview of message quality (inbox, spam).

#### Monitoring tools {#monitoring-tools}

**For on-premise installations**, you can use the following monitoring tools:

* The **[!UICONTROL Delivery throughput]** report gives you an overview of the entire platform's throughput for a given period. For more on this, see [this section](../../reporting/using/global-reports.md#delivery-throughput).
* Each delivery generates a broadcast statistics report for the different Internet service providers (ISPs). It shows some data quality and reputation metrics that may impact your deliverability, including the following numbers:
    * **[!UICONTROL Hard bounces]** indicate data quality. This number should be less than 2%.
    * **[!UICONTROL Soft bounces]** indicate reputation. This number should not be higher than 10% for any given ISP.
    
    For more on this, see the [Delivery statistics](../../reporting/using/global-reports.md#delivery-statistics) section.

#### Monitoring guidelines {#monitoring-guidelines}

**For on-premise installations**, here are some additional guidelines on deliverability monitoring:

* Regularly check the [delivery throughput](../../reporting/using/global-reports.md#delivery-throughput) for the whole platform to verify whether it is consistent with the original set-up.
* Check that [retries](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) are set up correctly (30 minutes for retry period and more than 20 retries) in delivery templates.
* Regularly verify that the [bounce](understanding-delivery-failures.md#bounce-mail-management) mailbox is accessible and that the account is not about to expire.
* Check each delivery throughput, accessible from the [delivery dashboard](delivery-dashboard.md), to make sure that it is consistent with the delivery content's validity (e.g. 'flash sales' should be delivered in minutes, not days).
* When using waves, verify that each wave has enough time to finish before the next one is triggered.
* Check that the number of errors and new [quarantines](understanding-quarantine-management.md) are consistent with other deliveries.
* Carefully consult the [delivery logs](delivery-dashboard.md#delivery-logs-and-history) in detail to check the kind of errors that are highlighted (denylists, DNS issues, anti-spam rules, etc.).

### Troubleshooting {#delivery-troubleshooting}

Specific actions can be performed when encountering issues with deliveries on **hybrid/on-premise deployments**:

* [Deliverability issues](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Image display issues](../../production/using/image-display-issues.md)
* [Delivery performance issues](delivery-performances.md)
* [Temporary files issues](../../production/using/temporary-files.md) - *on-premise customers only*

## General monitoring topics

**Monitor your deliveries:**

* [Monitor your deliveries in Campaign UI](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Campaign v8 documentation)
* [Delivery performances and best practices](delivery-performances.md)
* [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8 documentation - comprehensive guide for both v7 and v8)

**v7-specific configuration:**

* [Bounce mail management configuration](understanding-delivery-failures.md) (v7 hybrid/on-premise)
* [Quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8 documentation - comprehensive guide for both v7 and v8)
* [Quarantine configuration](understanding-quarantine-management.md) (v7 hybrid/on-premise)

**Track messages:**

* [Get started with message tracking](about-message-tracking.md)

## Related topics

* [Delivery statuses](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (Campaign v8 documentation)
