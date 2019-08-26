---
title: Personalization data
seo-title: Personalization data
description: Personalization data
seo-description: 
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
index: y
internal: n
snippet: y
---

# Personalization data{#personalization-data}

It is possible to use data in the message template to test transactional message personalization. This functionality is used to generate a preview or send a proof. If you install the **Deliverability** module, this data allows you to display a rendering of the messages for various internet access providers (**Inbox rendering**: for more on this, refer to [this section](https://helpx.adobe.com/campaign/classic/delivery/using/about-deliverability.html)).

The purpose of this data is to test your messages before their final delivery. These messages do not coincide with actual data to be processed by Message Center. However, the XML structure must be identical to that of the event stored in the execution instance, as shown below. 

![](assets/messagecenter_create_custo_006.png)

This information enables you to personalize message content using personalization tags (for more on this, refer to [Creating message content](https://helpx.adobe.com/campaign/standard/message-center/using/creating-message-content.html)).

1. In the message template, click the **[!UICONTROL Seed addresses]** tab.
1. In the event content, enter the test information in XML format.

   ![](assets/messagecenter_create_custo_001.png)

