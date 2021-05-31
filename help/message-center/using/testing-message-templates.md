---
solution: Campaign Classic
product: campaign
title: Managing seed addresses in transactional messages
description: Managing seed addresses in transactional messages
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
---
# Testing message templatess {#testing-message-templates}

## Managing seed addresses in transactional messages {#managing-seed-addresses-in-transactional-messages}

A seed address lets you display a preview of your message, send a proof, and test message personalization before email or SMS delivery. Seed addresses are linked to the delivery and cannot be used for other deliveries.

To create seed addresses in a transactional message, follow the steps below:

1. In the transactional message template, click the **[!UICONTROL Seed addresses]** tab.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Assign a label to it for easy selection later.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Enter the seed address (email or mobile phone depending on the communication channel). 

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Enter the external identifier: this optional field allows you to enter a business key (unique ID, name + email, etc.) that is common to all applications on your website, used to identify your profiles. If this field is also present in the Adobe Campaign marketing database, you can then reconcile an event with a profile in the database.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Insert test data (refer to [Personalization data](#personalization-data)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Click the **[!UICONTROL Add other seed addresses]** link, then click the **[!UICONTROL Add]** button.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Repeat the process to create as many addresses as you need.

   ![](assets/messagecenter_create_seedaddr_008.png)

Once the addresses are created, you can display their preview and personalization. Refer to [Transactional message preview](#transactional-message-preview).

## Personalization data {#personalization-data}

It is possible to use data in the message template to test transactional message personalization. This functionality is used to generate a preview or send a proof. If you install the **Deliverability** module, this data allows you to display a rendering of the messages for various internet access providers (**Inbox rendering**: for more on this, refer to [this section](../../delivery/using/inbox-rendering.md)).

The purpose of this data is to test your messages before their final delivery. These messages do not coincide with actual data to be processed by Message Center. However, the XML structure must be identical to that of the event stored in the execution instance, as shown below. 

![](assets/messagecenter_create_custo_006.png)

This information enables you to personalize message content using personalization tags (for more on this, refer to [Creating the message content](../../message-center/using/creating-the-message-template.md#creating-message-content)).

1. In the message template, click the **[!UICONTROL Seed addresses]** tab.
1. In the event content, enter the test information in XML format.

   ![](assets/messagecenter_create_custo_001.png)

## Transactional message preview {#transactional-message-preview}

Once you have created one or more seed addresses and the message body, you can preview the message and check its personalization.

1. In the message template, click the **[!UICONTROL Preview]** tab.

   ![](assets/messagecenter_preview_001.png)

1. Select **[!UICONTROL A seed address]** in the drop-down list.

   ![](assets/messagecenter_preview_002.png)

1. Select the seed address created previously to display the personalized message.

   ![](assets/messagecenter_create_seedaddr_009.png)

## Sending a proof {#sending-a-proof}

You can test message delivery by sending a proof to a previously created seed address.

Sending a proof involves the same process as for a regular delivery (for more on this, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)). However, to send a proof within Message Center you need to carry out the following operations beforehand:

* Create one or more seed addresses (refer to [Managing seed addresses in transactional messages](#managing-seed-addresses-in-transactional-messages)) with test data (refer to [Personalization data](#personalization-data)).
* Create the message content (refer to [Creating message content](../../message-center/using/creating-message-content.md)).

To send the proof:

1. Click the **[!UICONTROL Send a proof]** button in the delivery window.
1. Analyze the delivery.
1. Correct any errors and confirm the delivery.

   ![](assets/messagecenter_send_proof_001.png)

1. Check that the message was delivered to the seed address and that its content complies with your configuration.

   ![](assets/messagecenter_send_proof_002.png)

Proofs can be accessed in each template via the **[!UICONTROL Audit]** tab.

![](assets/messagecenter_send_proof_003.png)