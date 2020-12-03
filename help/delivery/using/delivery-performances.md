---
solution: Campaign Classic
product: campaign
title: Monitoring a delivery
description: Monitoring a delivery
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
---

# Monitoring a delivery{#monitoring-a-delivery}

## Delivery dashboard synchronization {#delivery-dashboard-synchronization}

From your delivery dashboard, you want to check the processed messages and delivery logs to be sure that your delivery was successfully sent.

Some indicators or status can be incorrect or not up-to-date, this may be resolved with the following solutions:

* If your delivery status is incorrect, check that all necessary approvals have been done for this delivery or that the **[!UICONTROL operationMgt]** and **[!UICONTROL deliveryMgt]** workflows are running without errors. This can also be due to the delivery using an affinity not configured on the sending instance.
* If your delivery indicators are still at zero and if you are on a mid-sourcing configuration, check the **[!UICONTROL Mid-sourcing (delivery counters)]** technical workflow. Start it if its status is not **[!UICONTROL Started]**. You can then try to recompute the indicators by right-clicking the relevant delivery in the Adobe Campaign explorer and selecting **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* If your delivery counter does not match your delivery, try to recompute the indicators by right-clicking the relevant delivery in the Adobe Campaign explorer and selecting **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** to resynchronize. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* If your delivery counter is not up-to-date for mid-sourcing deployments, check that the **[!UICONTROL Mid-Sourcing (Delivery counters)]** technical workflow is running. For more on this, refer to this [page](../../installation/using/mid-sourcing-deployment.md).

You can also track your deliveries with different reports via the delivery dashboard. For more on this, refer to this [section](../../reporting/using/delivery-reports.md).

## Performance issues checklist {#performance-issues}

If delivery performances are bad, you can check:

* **The size of the delivery**: Large deliveries can take longer to complete. MTA children are configured to handle a default batch size, which works for most instances, but need to be checked when deliveries are constantly slow.
* **The target of the delivery**: Delivery performances ban be affected by soft bounce errors, which are handled according to the retry configuration. The greater the number of errors, the more retries needed. 
* **The overall platform load**: When several large deliveries are being sent, the overall platform can be affected. You can also check IP reputation and deliverability issues. For more on this, refer to Adobe Campaign [Deliverability best practices guide](../../delivery/using/deliverability-key-points.md) and to [this page](../../delivery/using/about-deliverability.md).

Platform and database maintenance can also affect delivery sending performances. For more on this, refer to [this page](../../production/using/database-performances.md).

## Slow deliveries {#slow-deliveries}

After clicking the **[!UICONTROL Send]** button, your delivery seems to take longer than usual. This may be caused by different elements:

* Some email providers might have added your IP addresses to a denylist. In this case, check your broadlogs and consult [this section](../../delivery/using/about-deliverability.md).
* Your delivery might be too big to be processed quickly, this may occur with high JavaScript personalization or if your delivery weighs more than 60kbytes. Refer to Adobe Campaign [Delivery best practices](../../delivery/using/delivery-best-practices.md) to learn about content guidelines.
* Throttling might have occurred within the Adobe Campaign MTA. This is caused by:

    * Messages pended (**[!UICONTROL quotas met]** message): quotas declared by the declarative MX rules defined in Campaign have been met. For more information about this message, refer to [this page](../../delivery/using/deliverability-faq.md) . To learn more about MX rules, refer to [this page](../../delivery/using/technical-recommendations.md#mx-rules).
    * Messages pended (**[!UICONTROL dynamic flow control]** message): Campaign MTA has encountered errors when trying to deliver messages for a given ISP which causes a slowdown to avoid too big of an error density and thus facing potential denylist.

* A system issue can prevent servers from interacting together: this can slow down the whole sending process. Check the servers to ensure that there is no memory or resource issues which can impact Campaign in the process of getting the personalization data for example.

## Best practices for performance {#best-practices-performance}

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

## Scheduled deliveries {#scheduled-deliveries-}

If deliveries do not execute at exact scheduled date, it can be related to a difference between servers time zone. The mid-sourcing instance and the production instance can be in different time zones.

As an example, if the mid-sourcing instance is in Brisbane time zone and production instance is in Darwin time zone, both time zones are half an hour apart from each other, then in the audit log you would clearly see that if the delivery is scheduled for production at 11:56, the same delivery scheduled for mid would be at 12:26 which has a difference of half an hour.
