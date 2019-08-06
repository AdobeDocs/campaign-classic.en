---
title: Types of deliveries
seo-title: Types of deliveries
description: Types of deliveries
seo-description: 
page-status-flag: never-activated
uuid: 9975ab71-7aea-4bfb-9bb7-f16a9ab07543
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: fb5e59e7-982f-4532-8e9e-bb7e68e14364
index: y
internal: n
snippet: y
---

# Types of deliveries{#types-of-deliveries}

There are three types of delivery objects in Campaign:

## Single delivery {#single-delivery}

A **delivery** is a standalone delivery object that is executed once. It can be duplicated, prepared again, but as long as it is in its final state (canceled, stopped, finished), it cannot be reused.

Deliveries can be created either from the list of deliveries, or within a workflow via a [Delivery](../../workflow/using/delivery.md) activity.

Workflows also provide specific delivery activities according to the type of channel you want to use. For more on these activites, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

## Recurring delivery {#recurring-delivery}

A **recurring delivery** lets you create a new delivery each time the activity is executed. This avoids you having to create a new delivery for recurring tasks.

As an example, if you run this type of activity once a month, you will end up with 12 deliveries after a year.

Recurring deliveries are created within workflows via the Recurring delivery activity. An example of this activity being used is presented in this section: [Creating a recurring delivery in a targeting workflow](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Continuous delivery {#continuous-delivery}

A **continuous delivery** lets you add new recipients to an existing delivery, which avoids having to create a new delivery each time it is executed.

If an information in the delivery changes (content, name, etc.), a new delivery object is created at the delivery execution. If no information was changed, the same delivery object is reused and the delivery and tracking logs are added in the same object.

As an example, if you run this type of activity once a month, you will end up with a single delivery after a year (provided you did not make any change to the delivery).

Continuous deliveries are created whithin workflows via the Continuous delivery activity.
