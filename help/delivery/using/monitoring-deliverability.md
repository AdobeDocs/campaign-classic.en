---
product: campaign
title: Monitor deliverability in Adobe Campaign
description: Learn about tools and guidelines on deliverability monitoring in Adobe Campaign
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
---
# Monitor your deliverability{#monitoring-deliverability}

Below you will find details on the different monitoring tools provided by Adobe Campaign, as well as some additional guidelines on leveraging the features offered by Adobe Campaign to monitor your platform's deliverability.

## About deliverability monitoring {#about-deliverability-monitoring}

This feature is available through a dedicated package in Adobe Campaign. To use it, this package must be installed. Once done, restart the server for the package to be taken into account.
* For hosted and hybrid clients, **Deliverability monitoring** is configured on your instance by Adobe technical support and consultants. For more information, contact your Adobe Account executive.
 
* For on-premise installations, you must install the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. For more on this, see [Instal Campaign Classic standard packages](../../installation/using/installing-campaign-standard-packages.md).
 
In Adobe Campaign Classic, **Deliverability monitoring** is managed by the **[!UICONTROL Refresh for deliverability]** workflow. It is installed by default on all instances and lets you initialize the list of bounce mail qualification rules, the list of domains and the list of MXs. Once the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package is installed, this workflow runs nightly to regularly update the list of rules and enables you to actively manage platform deliverability.

The Deliverability package gives you access to:

* The [Inbox rendering report](inbox-rendering.md) which enables you to preview your messages on major email clients in order to scan content and reputation.
* Overview of message quality (inbox, spam).

## Monitoring tools {#monitoring-tools}

You can also use the following tools:

* The **[!UICONTROL Delivery throughput]** report gives you an overview of the entire platform's throughput for a given period. For more on this, see [this section](../../reporting/using/global-reports.md#delivery-throughput).
* Each delivery generates a broadcast statistics report for the different Internet service providers (ISPs). It shows some data quality and reputation metrics that may impact your deliverability, including the following numbers:
    * **[!UICONTROL Hard bounces]** indicate data quality. This number should be less than 2%.
    * **[!UICONTROL Soft bounces]** indicate reputation. This number should not be higher than 10% for any given ISP.
    
    For more on this, see the [Delivery statistics](../../reporting/using/global-reports.md#delivery-statistics) section.
* More generally, the [delivery dashboard](about-delivery-monitoring.md) gives you access to:
    * the [delivery summary](delivery-dashboard.md#delivery-summary), which shows the detail of the sending and the number of messages to send, processed and sent with success;
    * the [delivery logs and history](delivery-dashboard.md#delivery-logs-and-history), which show which target has been excluded and why;
    * the [tracking logs](delivery-dashboard.md#tracking-logs), which show tracking information such as opens and clicks.

## Monitoring guidelines {#monitoring-guidelines}

Here are some additional guidelines on deliverability monitoring:

* Regularly check the [delivery throughput](../../reporting/using/global-reports.md#delivery-throughput) for the whole platform to verify whether it is consistent with the original set-up.
* Check that [retries](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) are set up correctly (30 minutes for retry period and more than 20 retries) in delivery templates.
* Regularly verify that the [bounce](understanding-delivery-failures.md#bounce-mail-management) mailbox is accessible and that the account is not about to expire.
* Check each delivery throughput, accessible from the [delivery dashboard](delivery-dashboard.md), to make sure that it is consistent with the delivery content's validity (e.g. 'flash sales' should be delivered in minutes, not days).
* When using waves, verify that each wave has enough time to finish before the next one is triggered. See the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html#sending-using-multiple-waves){target="_blank"}.
* Check that the number of errors and new [quarantines](understanding-quarantine-management.md) are consistent with other deliveries.
* Carefully consult the [delivery logs](delivery-dashboard.md#delivery-logs-and-history) in detail to check the kind of errors that are highlighted (denylists, DNS issues, anti-spam rules, etc.).
