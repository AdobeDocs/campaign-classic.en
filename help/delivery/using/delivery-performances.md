---
product: campaign
title: Delivery performances best practices
description: Learn more about delivery performances and best practices.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
---
# Delivery performances best practices {#delivery-performances}

We recommend following the guidelines below to ensure your deliveries perform well, as well as the checks the perform if you encounter deliveries issues.

**Related topics:**

* [Delivery dashboard](delivery-dashboard.md)
* [Delivery troubleshooting](delivery-troubleshooting.md)
* [About deliverability](about-deliverability.md)

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

## Performance issues checklist {#performance-issues}

If delivery performances are bad, you can check:

* **The size of the delivery**: Large deliveries can take longer to complete. MTA children are configured to handle a default batch size, which works for most instances, but need to be checked when deliveries are constantly slow.
* **The target of the delivery**: Delivery performances ban be affected by soft bounce errors, which are handled according to the retry configuration. The greater the number of errors, the more retries needed. 
* **The overall platform load**: When several large deliveries are being sent, the overall platform can be affected. You can also check IP reputation and deliverability issues. For more on this, refer to [this section](about-deliverability.md) and to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

Platform and database maintenance can also affect delivery sending performances. For more on this, refer to [this page](../../production/using/database-performances.md).
