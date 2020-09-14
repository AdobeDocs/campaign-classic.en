---
title: Monitoring a delivery
seo-title: Monitoring a delivery
description: Monitoring a delivery
seo-description: 
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
---

# Monitoring a delivery{#monitoring-a-delivery}

The **delivery dashboard** is key to monitor your deliveries and eventual issues encountered during the sending of messages.

**Related topics:**

* [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md)
* [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md)
* [Delivery best practices](../../delivery/using/delivery-best-practices.md)
* [Managing deliverability](../../delivery/using/about-deliverability.md)

## Delivery dashboard {#delivery-dashboard}

To view the information on a delivery, edit it, view the dashboard and click the available tabs.

Tab contents may no longer be changed once the delivery has been sent. 

![](assets/s_ncs_user_del_details.png)

### Delivery summary {#delivery-summary}

The **[!UICONTROL Summary]** tab contains the characteristics of the delivery: delivery status, channel used, information about the sender, subject, information concerning execution. For more on this, refer to [Number of messages sent](#number-of-messages-sent).

The **[!UICONTROL reports]** link lets you look at a set of reports concerning the delivery action: general delivery report, detailed report, delivery report, distribution of failed messages, opening rate, clicks and transactions, etc. The contents of this tab can be configured according to your requirements. For more information, refer to [this section](../../reporting/using/delivery-reports.md).

### Delivery logs and history {#delivery-logs-and-history}

The **[!UICONTROL Delivery]** tab gives a history of the occurrences in this delivery. It contains the delivery logs, i.e. the list of messages sent and their status and the associated messages.

For a delivery, you can display (for example) only recipients with a failed delivery or an address in quarantine. To do this, click the **[!UICONTROL Filters]** button and select **[!UICONTROL By state]**. Then select the state in the drop-down list.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Various statuses are listed on [this page](#delivery-statuses).

>[!NOTE]
>
>The **[!UICONTROL Display the mirror page for this message...]** link lets you view the mirror page for the contents of the delivery selected from the list in a new window. The mirror page is available only for deliveries for which HTML content has been defined. For more on this, refer to [Generating the mirror page](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### Tracking logs {#tracking-logs}

The **[!UICONTROL Tracking]** tab lists the tracking history for this delivery. This tab displays tracking data for the messages sent, i.e. all URLs subject to tracking by Adobe Campaign. The tracking data is updated hourly.

>[!NOTE]
>
>If tracking isn't enabled for a delivery, this tab isn't displayed.

Tracking configuration is performed at the appropriate stage in the delivery wizard. See [How to configure tracked links](../../delivery/using/how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** data is interpreted in the delivery reports. See [this section](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Delivery audit {#delivery-audit-}

The **[!UICONTROL Audit]** tab contains the delivery log and all the messages concerning the proofs. The **[!UICONTROL Refresh]** button lets you update the data. Use the **[!UICONTROL Filters]** button to define a filter on the data.

Special icons enable you to identify errors or warnings. See [Analyzing the delivery](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

The **[!UICONTROL Proofs]** sub-tab lets you view the list of proofs that have been sent.

![](assets/s_ncs_user_delivery_log_tab.png)

You can modify the information displayed in this window (and that of the **[!UICONTROL Delivery]** and **[!UICONTROL Tracking]** tabs) by selecting the columns to be displayed. To do this, click the **[!UICONTROL Configure list]** icon located in the lower right-hand corner. For more on configuring list display, refer to [this section](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Delivery dashboard synchronization {#delivery-dashboard-synchronization}

From your delivery dashboard, you want to check the processed messages and delivery logs to be sure that your delivery was successfully sent.

Some indicators or status can be incorrect or not up-to-date, this may be resolved with the following solutions:

* If your delivery status is incorrect, check that all necessary approvals have been done for this delivery or that the **[!UICONTROL operationMgt]** and **[!UICONTROL deliveryMgt]** workflows are running without errors. This can also be due to the delivery using an affinity not configured on the sending instance.
* If your delivery indicators are still at zero and if you are on a mid-sourcing configuration, check the **[!UICONTROL Mid-sourcing (delivery counters)]** technical workflow. Start it if its status is not **[!UICONTROL Started]**. You can then try to recompute the indicators by right-clicking the relevant delivery in the Adobe Campaign explorer and selecting **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* If your delivery counter does not match your delivery, try to recompute the indicators by right-clicking the relevant delivery in the Adobe Campaign explorer and selecting **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** to resynchronize. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* If your delivery counter is not up-to-date for mid-sourcing deployments, check that the **[!UICONTROL Mid-Sourcing (Delivery counters)]** technical workflow is running. For more on this, refer to this [page](../../installation/using/mid-sourcing-deployment.md).

You can also track your deliveries with different reports via the delivery dashboard. For more on this, refer to this [section](../../reporting/using/delivery-reports.md).

## Performance issues {#performance-issues}

### Checklist {#checklist-}

If delivery performances are bad, you can check:

* **The size of the delivery**: Large deliveries can take longer to complete. MTA children are configured to handle a default batch size, which works for most instances, but need to be checked when deliveries are constantly slow.
* **The target of the delivery**: Delivery performances ban be affected by soft bounce errors, which are handled according to the retry configuration. The greater the number of errors, the more retries needed. 
* **The overall platform load**: When several large deliveries are being sent, the overall platform can be affected. You can also check IP reputation and deliverability issues. For more on this, refer to Adobe Campaign [Deliverability best practices guide](../../delivery/using/deliverability-key-points.md) and to [this page](../../delivery/using/about-deliverability.md).

Platform and database maintenance can also affect delivery sending performances. For more on this, refer to [this page](../../production/using/database-performances.md).

### Slow deliveries {#slow-deliveries}

After clicking the **[!UICONTROL Send]** button, your delivery seems to take longer than usual. This may be caused by different elements:

* Some email providers might have added your IP addresses to a denylist. In this case, check your broadlogs and consult [this section](../../delivery/using/about-deliverability.md).
* Your delivery might be too big to be processed quickly, this may occur with high JavaScript personalization or if your delivery weighs more than 60kbytes. Refer to Adobe Campaign [Delivery best practices](../../delivery/using/delivery-best-practices.md) to learn about content guidelines.
* Throttling might have occurred within the Adobe Campaign MTA. This is caused by:

    * Messages pended (**[!UICONTROL quotas met]** message): quotas declared by the declarative MX rules defined in Campaign have been met. For more information about this message, refer to [this page](../../delivery/using/deliverability-faq.md) . To learn more about MX rules, refer to [this page](../../delivery/using/technical-recommendations.md#mx-rules).
    * Messages pended (**[!UICONTROL dynamic flow control]** message): Campaign MTA has encountered errors when trying to deliver messages for a given ISP which causes a slowdown to avoid too big of an error density and thus facing potential denylist.

* A system issue can prevent servers from interacting together: this can slow down the whole sending process. Check the servers to ensure that there is no memory or resource issues which can impact Campaign in the process of getting the personalization data for example.

### Best practices for performance {#best-practices-performance}

* Do not keep deliveries in failed state on the instance, as this maintains temporary tables and impacts the performance.

* Remove deliveries which are no longer needed.

* Inactive recipients in the last 12 months to be removed from the database to maintain address quality.

* Do no try to schedule large deliveries together. There is a gap of 5-10 minutes to spread the load uniformly over the system. Coordinate the scheduling of deliveries with the other members of your team to ensure the best performance. When the marketing server is handling many different tasks at the same time, it can slow down performance.

* Keep the size of your emails as low as possible. The recommended maximum size of an email is about 35KB. The size of an email delivery generates a certain amount of volume in the sending servers.

* Large deliveries, such as deliveries to over one million recipients, need space in the sending queues. This alone is not an issue for the server, but when combined with dozens of other large deliveries all going out at the same time, it can introduce a sending delay.

* Personalization in emails pulls data out of the database for each recipient. If there are many personalization elements, that increases the amount of data needed to prepare the delivery.

* Index addresses. To optimize the performance of the SQL queries used in the application, an index can be declared from the main element of the data schema.

>[!NOTE]
>
>ISPs would deactivate addresses after a period of inactivity. Bounced messages are sent to senders to inform them about this new status.

## Delivery statuses {#delivery-statuses}

While sending a delivery, you may face the following status on your delivery dashboard:

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definitions and solutions<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Not applicable<br /> </td> 
   <td> The delivery was taken into account by the server (MTA) but not processed.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignored<br /> </td> 
   <td> The delivery was not sent to the recipient because of an error with his address. It was either on denylist, quarantined, not provided or a duplicate. <br /> </td> 
  </tr> 
  <tr> 
   <td> Sent<br /> </td> 
   <td> The delivery was correctly sent to the message provider (but the recipient did not necessarily receive it).<br /> </td> 
  </tr> 
  <tr> 
   <td> Failed<br /> </td> 
   <td> The delivery could not reach the recipient because of an invalid address or a full inbox for example. It can also be linked to an issue with personalization blocks since they can generate errors when the schemas do not match the delivery mapping. See <a href="#failed-status" target="_blank">Failed status</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Taken into account by the service provider<br /> </td> 
   <td> The SMS service provider received the delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Received on mobile<br /> </td> 
   <td> The recipient received the SMS on their mobile device.<br /> </td> 
  </tr> 
  <tr> 
   <td> Pending<br /> </td> 
   <td> The delivery is ready to be sent and is going to be processed by the delivery server (MTA). See <a href="#pending-status" target="_blank">Pending status</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivery canceled<br /> </td> 
   <td> The delivery was canceled by an operator.<br /> </td> 
  </tr> 
  <tr> 
   <td> Prepared<br /> </td> 
   <td> Intermediary status used only for external connectors such as the mobile channel. It follows the 'Pending' status and is the external connector that will determine the following status.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sent to the service provider<br /> </td> 
   <td> The delivery was sent to the SMS service provider but not received yet.<br /> </td> 
  </tr> 
 </tbody> 
</table>

To learn how to optimize the deliverability of your Adobe Campaign emails, refer to Adobe Campaign [Deliverability best practices guide](../../delivery/using/deliverability-key-points.md)  and to [this page](../../delivery/using/about-deliverability.md).

### Pending status {#pending-status}

After confirming your delivery, you can see that the status of your delivery is **[!UICONTROL Pending]**. This status means that the execution process is waiting on the availability of some resources.

The **[!UICONTROL Pending]** status can first mean that your delivery has been scheduled and is pending until the given date. For more on this, refer to the [Delivery scheduling](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) section.

If your delivery is not being sent and its status remains **[!UICONTROL Pending]**, it can be the result of:

* The MTA (Message Transfert Agent), that runs modules and processes on the delivery server and that manages email sending, may have not been started, or need to be restarted. To check this and to start the module if necessary, apply the following steps:

    * Check that your `mta@<instance>` modules are launched on your MTA servers.

    ```
    nlserver pdump
    HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
    [...]
    mta@<INSTANCENAME> (9268) - 23.0 Mb
    [...]
    ```

    * If the MTA is not listed, start it with the following command:

    ```
    nlserver start mta@<INSTANCENAME>
    ```

    >[!NOTE]
    >
    >Replace `<INSTANCENAME>` with the name of your instance (production, development, etc.). The instance name is identified via the configuration files: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* The delivery may be using an affinity not configured on the sending server. In this case, check the configuration of the traffic management (IP affinity) and use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the MTA that manages the affinity. For more information on affinities, refer to [this section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* When the delivery preparation is pending, there can be too many campaigns running, which blocked the status update of the delivery. To solve this, go to **[!UICONTROL Options]** and increase the value of **[!UICONTROL NmsOperation_LimitConcurrency]** (default is 10). Do not run more campaigns than the value assigned to this specific option.

### Failed status {#failed-status}

If an email delivery's status is **[!UICONTROL Failed]**, it can be linked to an issue with personalization blocks. Personalization blocks in a delivery can generate errors when the schemas do not match the delivery mapping, for example.

Delivery logs are key to learn why a delivery failed. Here are possible errors that you can detect from delivery logs:

* If recipient messages are failing with an "Unreachable" error stating: **Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent**, the cause of this issue is almost always a personalization within the HTML attempting to call upon a table or field that has not been defined or mapped in the upstream targeting or in the delivery's target mapping.

  To correct this, the workflow and delivery content need to be reviewed to determine specifically what personalization is attempting to call the table in question and whether or not the table can be mapped. From there, either removing the call to this table in the HTML or fixing the mapping to the delivery would be the path to resolution.

* In mid-sourcing deployment model, the following message can appear in the delivery logs: **Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'**.

  The cause is linked to performance issues. It means that the marketing instance spend too much time building data before sending it to the mid-sourcing server.

  To solve this, we recommend performing a vacuum and reindex on the database. For more information on database maintenance, refer to [this section](../../production/using/recommendations.md).

  You should also restart all workflows with a scheduled activity, and all workflows in failed status. Refer to [this section](../../workflow/using/scheduler.md).

* When a delivery fails, the following error can appear in the delivery logs: **DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.**

  Usually, this error means that there is a personalization field or block within the email that has more than one values for the recipient. A personalization block is being used and it is fetching more than one record for a particular recipient.

  To solve this, check the personalization data used, and then check the target for recipients that have more than one entry for any of those fields. You can also use a **[!UICONTROL Deduplication]** activity in the targeting workflow prior to the delivery activity to check there is only one personalization field at a time. For more information on deduplication, refer to [this page](../../workflow/using/deduplication.md).

* Some delivery can fail with an "Unreachable" error stating: "Inbound email bounce (rule 'Auto_replies' has matched this bounce). This means that the delivery succeeded but Adobe Campaign received an auto-reply from the recipient (e.g. an "Out of office" reply) that matched the 'Auto_replies' inbound email rules. The auto-reply email is ignored by Adobe Campaign, and the recipient's address will not be sent to quarantines.

**Related topics:**

* [Delivery logs and history](#delivery-logs-and-history)
* [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md)
* [Delivery failure types and reasons](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Number of messages sent {#number-of-messages-sent}

You can access deliveries from the delivery list, via the **[!UICONTROL Campaign Management > Deliveries]** node of the tree.

By default, the list of deliveries contains the names and statuses of the deliveries created in the selected node. It also shows the number of messages to send, processed and sent with success.

* The number of **[!UICONTROL Messages to send]** corresponds to the number of recipients targeted after analysis and prior to delivery.
* The number of messages in the **[!UICONTROL Success]** column corresponds to the number of messages sent by the server and received by the recipients.
* The number of **[!UICONTROL Processed]** messages corresponds to the number of messages received plus the number of messages with errors.

The delivery dashboard lets you track the number of messages sent.

>[!NOTE]
>
>For large deliveries, you may wish to update these values. To do this, select the delivery in question and then right-click it. Select **[!UICONTROL Action > Recompute delivery and tracking indicators...]** and then use the wizard to update this information.

## Scheduled deliveries {#scheduled-deliveries-}

If deliveries do not execute at exact scheduled date, it can be related to a difference between servers time zone. The mid-sourcing instance and the production instance can be in different time zones.

As an example, if the mid-sourcing instance is in Brisbane time zone and production instance is in Darwin time zone, both time zones are half an hour apart from each other, then in the audit log you would clearly see that if the delivery is scheduled for production at 11:56, the same delivery scheduled for mid would be at 12:26 which has a difference of half an hour.
