---
solution: Campaign Classic
product: campaign
title: Troubleshooting
description: Learn more about delivery performances and how to troubleshoot issues related to delivery monitoring.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
---
# Delivery sending troubleshooting {#delivery-troubleshooting}

This section lists common issues you may encounter when sending deliveries, and how to troubleshoot them.

Additionally, make sure you follow the best practices and checklist detailed in [this page](../../delivery/using/delivery-performances.md) to ensure your deliveries perform well.

**Related topics:**

* [Delivery statuses](../../delivery/using/delivery-statuses.md)
* [Delivery dashboard](../../delivery/using/delivery-dashboard.md)
* [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md)

## Slow deliveries {#slow-deliveries}

After clicking the **[!UICONTROL Send]** button, your delivery seems to take longer than usual. This may be caused by different elements:

* Some email providers might have added your IP addresses to a denylist. In this case, check your broadlogs and consult [this section](../../delivery/using/about-deliverability.md).

* Your delivery might be too big to be processed quickly, this may occur with high JavaScript personalization or if your delivery weighs more than 60kbytes. Refer to Adobe Campaign [Delivery best practices](../../delivery/using/delivery-best-practices.md) to learn about content guidelines.

* Throttling might have occurred within the Adobe Campaign MTA. This is caused by:

    * Messages pended (**[!UICONTROL quotas met]** message): quotas declared by the declarative MX rules defined in Campaign have been met. For more information about this message, refer to [this page](../../delivery/using/deliverability-faq.md). To learn more about MX rules, refer to [this section](../../installation/using/email-deliverability.md#about-mx-rules).

    * Messages pended (**[!UICONTROL dynamic flow control]** message): Campaign MTA has encountered errors when trying to deliver messages for a given ISP which causes a slowdown to avoid too big of an error density and thus facing potential denylist.

* A system issue can prevent servers from interacting together: this can slow down the whole sending process. Check the servers to ensure that there is no memory or resource issues which can impact Campaign in the process of getting the personalization data for example.

## Scheduled deliveries {#scheduled-deliveries-}

If deliveries do not execute at exact scheduled date, it can be related to a difference between servers time zone. The mid-sourcing instance and the production instance can be in different time zones.

As an example, if the mid-sourcing instance is in Brisbane time zone and production instance is in Darwin time zone, both time zones are half an hour apart from each other, then in the audit log you would clearly see that if the delivery is scheduled for production at 11:56, the same delivery scheduled for mid would be at 12:26 which has a difference of half an hour.

## Failed status {#failed-status}

If an email delivery's status is **[!UICONTROL Failed]**, it can be linked to an issue with personalization blocks. Personalization blocks in a delivery can generate errors when the schemas do not match the delivery mapping, for example.

Delivery logs are key to learn why a delivery failed. Here are possible errors that you can detect from delivery logs:

* Recipient messages are failing with an "Unreachable" error stating:

  ```
  Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
  ```

  The cause of this issue is almost always a personalization within the HTML attempting to call upon a table or field that has not been defined or mapped in the upstream targeting or in the delivery's target mapping.

  To correct this, the workflow and delivery content need to be reviewed to determine specifically what personalization is attempting to call the table in question and whether or not the table can be mapped. From there, either removing the call to this table in the HTML or fixing the mapping to the delivery would be the path to resolution.

* In mid-sourcing deployment model, the following message can appear in the delivery logs:

  ```
  Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
  ```

  The cause is linked to performance issues. It means that the marketing instance spend too much time building data before sending it to the mid-sourcing server.

  To solve this, we recommend performing a vacuum and reindex on the database. For more information on database maintenance, refer to [this section](../../production/using/recommendations.md).

  You should also restart all workflows with a scheduled activity, and all workflows in failed status. Refer to [this section](../../workflow/using/scheduler.md).

* When a delivery fails, the following error can appear in the delivery logs:

  ```
  DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
  ```

  Usually, this error means that there is a personalization field or block within the email that has more than one values for the recipient. A personalization block is being used and it is fetching more than one record for a particular recipient.

  To solve this, check the personalization data used, and then check the target for recipients that have more than one entry for any of those fields. You can also use a **[!UICONTROL Deduplication]** activity in the targeting workflow prior to the delivery activity to check there is only one personalization field at a time. For more information on deduplication, refer to [this page](../../workflow/using/deduplication.md).

* Some delivery can fail with an "Unreachable" error stating: 

  ```
  Inbound email bounce (rule 'Auto_replies' has matched this bounce).
  ```

  This means that the delivery succeeded but Adobe Campaign received an auto-reply from the recipient (e.g. an "Out of office" reply) that matched the 'Auto_replies' inbound email rules.
  
  The auto-reply email is ignored by Adobe Campaign, and the recipient's address will not be sent to quarantines.
