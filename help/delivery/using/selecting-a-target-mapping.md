---
product: campaign
title: Select a target mapping
description: Learn how to target mapping
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
---
# Select a target mapping{#selecting-a-target-mapping}

By default, delivery templates target **[!UICONTROL Recipients]**. Their target mapping therefore uses the fields of the **nms:recipient** table. Adobe Campaign offers other target mappings for your deliveries, to be used based on your needs. 

![](assets/delivery_select_mapping.png)

These mappings are as follows:

|  Name  | Use  | Standard schema  |
|---|---|---|
|  Recipients  | Deliver to recipients of the Adobe Campaign database  | nms:recipient  |
|  Visitors  | Deliver to visitors whose profiles have been collected via referral (viral marketing) or via social networks (Facebook, X - formerly known as Twitter) for instance.  | mns:visitor  |
|  Subscriptions  | Deliver to recipients who are subscribed to an information service such as a newsletter  | nms:subscription  |
|  Visitor subscriptions  | Deliver to visitors who are subscribed to an information service  | nms:visitorSub  |
|  Service  | Publish to a X account or a Facebook page  | nms:service  |
|  Operators  | Deliver to Adobe Campaign operators  | nms:operator  |
|  External file  | Deliver via a file that contains all information needed for delivery  | No linked schema, no target entered  |

>[!NOTE]
>
>You can also create new target mappings. This operation is reserved for expert users. For more information, refer to [this section](../../configuration/using/target-mapping.md).
