---
product: campaign
title: Create event types
description: Learn how to create event types that will match the transactional messages you want to send in Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
TQID: https://experienceleague.adobe.com/WfR-CUGmR3XeEQgBwd22RZPpSMF0Gja-7GewIIIxWug
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
subfeature_v2: []
---
# Create event types {#creating-event-types}



To make sure each event can be changed into a personalized message, you first need to create **event types**.

When [creating a message template](../../message-center/using/creating-the-message-template.md), you will select the type of event that matches the message you want to send.

>[!IMPORTANT]
>
>You must create event types before being able to use them in message templates.

To create event types that will be processed by Adobe Campaign, follow the steps below:

1. Log on to the **control instance**.

1. Go to the **[!UICONTROL Administration > Platform > Enumerations]** folder of the tree.

1. Select **[!UICONTROL Event type]** from the list.

1. Click **[!UICONTROL Add]** to create an enumeration value. This can be an order confirmation, password change, order delivery change, etc.

    ![](assets/messagecenter_eventtype_enum_001.png)

    >[!IMPORTANT]
    >
    >Each event type must match a value in the **[!UICONTROL Event type]** enumeration.

1. Once the itemized list values have been created, log off and back on to your instance for the creation to be effective.

>[!NOTE]
>
>Learn more how to **work with enumerations** in [Adobe Campaign v8 (console) documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.



