---
product: campaign
title: Select a target mapping
description: Learn how to target mapping
feature: Delivery Templates
hide: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
TQID: 'https://experienceleague.adobe.com/VpmfQdFoJ2Lfzetqx-s5MAdFdTTEsHxz2ISL15wNXIo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: fc09322a-8f3d-5905-be3d-96adfa806a40
    internal-label: Delivery Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
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
