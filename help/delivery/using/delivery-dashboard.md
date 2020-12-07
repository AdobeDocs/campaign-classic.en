---
solution: Campaign Classic
product: campaign
title: Delivery monitoring interface
description: Learn more about the interface available to monitor deliveries.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
---

# Delivery dashboard {#delivery-dashboard}

The **delivery dashboard** is key to monitor your deliveries and eventual issues encountered during the sending of messages.

It allows you to retrieve information on a delivery and edit it if necessary. Note that tab contents may no longer be changed once the delivery has been sent.

![](assets/s_ncs_user_del_details.png)

Here are the information you can monitor using the several tabs that are available in the dashboard:

* [Delivery summary](#delivery-summary)
* [Delivery reports](#delivery-reports)
* [Delivery logs, history and exclusions](#delivery-logs-and-history)
* [Delivery tracking logs and history](#tracking-logs)
* [Delivery rendering](#delivery-rendering)
* [Delivery audit](#delivery-audit-)

<!-->
Lister aussi tout ce à quoi on a accès dans le delivery dashboard (ce qui est décrit dessous) : logs, rapports, inbox rendering, mirror page, …etc.
-->

**Related topics:**

* [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md)
* [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md)
* [Delivery best practices](../../delivery/using/delivery-best-practices.md)
* [Managing deliverability](../../delivery/using/about-deliverability.md)

## Delivery summary {#delivery-summary}

The **[!UICONTROL Summary]** tab contains the characteristics of the delivery: delivery status, channel used, information about the sender, subject, information concerning execution. For more on this, refer to [Number of messages sent](#number-of-messages-sent).

The **[!UICONTROL reports]** link lets you look at a set of reports concerning the delivery action: general delivery report, detailed report, delivery report, distribution of failed messages, opening rate, clicks and transactions, etc. The contents of this tab can be configured according to your requirements. For more information, refer to [this section](../../reporting/using/delivery-reports.md).

## Delivery reports {#delivery-reports}

<!--parler de reports + screenshot, ou section à part?-->

## Delivery logs, history and exclusions {#delivery-logs-and-history}

<!--4. Dans Delivery logs and history, montrer le lien ‘Display the mirror page for this message’-->

The **[!UICONTROL Delivery]** tab gives a history of the occurrences in this delivery. It contains the delivery logs, i.e. the list of messages sent and their status and the associated messages.

For a delivery, you can display (for example) only recipients with a failed delivery or an address in quarantine. To do this, click the **[!UICONTROL Filters]** button and select **[!UICONTROL By state]**. Then select the state in the drop-down list.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Various statuses are listed on [this page](#delivery-statuses).

>[!NOTE]
>
>The **[!UICONTROL Display the mirror page for this message...]** link lets you view the mirror page for the contents of the delivery selected from the list in a new window. The mirror page is available only for deliveries for which HTML content has been defined. For more on this, refer to [Generating the mirror page](../../delivery/using/sending-messages.md#generating-the-mirror-page).

## Delivery tracking logs and history {#tracking-logs}

The **[!UICONTROL Tracking]** tab lists the tracking history for this delivery. This tab displays tracking data for the messages sent, i.e. all URLs subject to tracking by Adobe Campaign. The tracking data is updated hourly.

>[!NOTE]
>
>If tracking isn't enabled for a delivery, this tab isn't displayed.

Tracking configuration is performed at the appropriate stage in the delivery wizard. See [How to configure tracked links](../../delivery/using/how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** data is interpreted in the delivery reports. See [this section](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

<!--Ajouter une section sur Inbox Rendering + lien-->

## Delivery rendering {#delivery-rendering}

## Delivery audit {#delivery-audit-}

The **[!UICONTROL Audit]** tab contains the delivery log and all the messages concerning the proofs. The **[!UICONTROL Refresh]** button lets you update the data. Use the **[!UICONTROL Filters]** button to define a filter on the data.

Special icons enable you to identify errors or warnings. See [Analyzing the delivery](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

The **[!UICONTROL Proofs]** sub-tab lets you view the list of proofs that have been sent.

![](assets/s_ncs_user_delivery_log_tab.png)

You can modify the information displayed in this window (and that of the **[!UICONTROL Delivery]** and **[!UICONTROL Tracking]** tabs) by selecting the columns to be displayed. To do this, click the **[!UICONTROL Configure list]** icon located in the lower right-hand corner. For more on configuring list display, refer to [this section](../../platform/using/adobe-campaign-workspace.md#configuring-lists).
