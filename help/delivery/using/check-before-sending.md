---
product: campaign
title: Check before sending
description: Once your message is ready, perform all checks before sending
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
role: User
hide: true
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
TQID: https://experienceleague.adobe.com/ngnYPos--1A5p7WN-fJnxaLt-yHG50lWHid4wbbyVZw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
---
# Perform all checks before sending {#perform-all-checks}

Once your message is ready, make sure its content is displayed correctly, on all devices, and does not contain any errors such as wrong personalization or broken links.

Before sending your message, also ensure that the parameters and configuration are consistent with the delivery.

## Why validation is key {#validation-is-key}

Before sending a delivery, you need to ensure that your recipients will receive the message that you really want to send them. To do this, you need to validate the message content and delivery parameters.

This step enables you to detect possible errors and fix them before delivering to your main target.

The steps for validating a delivery are presented [in this section](steps-validating-the-delivery.md).

## Inbox rendering {#inbox-and-email-rendering}

Inbox rendering enables you to preview your messages on major email clients, scan content and reputation, discover how recipients are reading messages.

**Tips**:

* You can view the sent message in the different contexts in which it may be received: webmail, message service, mobile, etc.

* Inbox rendering capabilities are crucial to identifying whether your email campaigns successfully make it past the filters of major ISPs (Internet Service Providers) and webmail services. Such tools send a pre-flight copy of an email to a network of test inboxes, so you can see how the message will display, or render, across these services. They may also include reports and code correction options that help you quickly identify and make fixes that improve deliverability.

Learn more [in this section](inbox-rendering.md).

## Proof messages {#proof-messages}

Sending proofs enables you to check the opt-out link, mirror page and any other links, validate the message, verify that images are displayed, detect possible errors, etc. You may also want to check your design and rendering on different devices.

Learn more [in this section](steps-validating-the-delivery.md#sending-a-proof).

## Set up A/B testing deliveries {#a-b-testing-deliveries}

If you have several contents for an email delivery, you can use A/B testing to find out which version will have the biggest impact on the targeted population.

**Tips**:

* Send the different versions to some of your recipients

* Select the one with the highest success rate and send it to the rest of your target

Learn more [in this section](get-started-a-b-testing.md).

## Make sure your message is delivered {#make-sure-your-message-is-delivered}

As a final step, maximize your chances and leverage the power of Adobe Campaign Classic to ensure that your message will be indeed delivered to the relevant recipients.

### Go through a validation process

You can define a full validation process, involving Adobe Campaign operators and groups, to validate both the target and the message content. This will ensure full monitoring and control of the various processes of the campaign: targeting, content, budget, extraction, and sending a proof. Depending on their permissions, users will be notified, receive proofs and be able to validate or reject the message. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md).

### Use waves

You can progressively increase the volume sent using waves. This will avoid your messages being marked as spam or when you want to restrict the number of messages per day. Using waves you can divide deliveries into several batches instead of sending high volumes of messages at the same time. Learn more [in this section](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Prioritize messages

You can set the sending order for your deliveries by stating the priority level. To do so:

1. Edit the delivery properties, and select the **[!UICONTROL Delivery]** tab.

1. Define the priority level for the delivery on a scale from **[!UICONTROL Very low]** to **[!UICONTROL Very high]**.

>[!NOTE]
>
>It is not possible to define the order of sending messages from within a delivery.

### Setup IP Affinities

To better control the outbound SMTP traffic, you can manage affinities by defining which specific IP addresses can be used for each affinity. This lets you restrict the number of emails for specific deliveries towards machines or output addresses. For example, you can use one affinity per country or sub-domain. You can then create one typology per country and link each affinity to the corresponding typology.

You can:

* Define the IP affinities in the serverConf.xml configuration file. [Learn more](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* For each IPAffinity element, declare the IP addresses that can be used. [Learn more](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In the [typology](../../campaign-opt/using/about-campaign-typologies.md) of your choice, use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the delivery server (MTA) which manages the said affinity. [Learn more](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Once the email is sent, check the header to verify which IP address the delivery was sent from. Your email administrator should help you obtain the header information.

* For SMS deliveries, make sure that the SMS channel has a dedicated affinity limited to **one** application server container. [Learn more](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>Most of these steps can only be performed by an expert user.

### Use typologies

You can use typology rules to exclude part of the target based on specific criteria. This guarantees that the messages sent best meet the needs and expectations of customers, in keeping with company communication policies. For example, you can filter the recipients who are underage from the target of your newsletter. Learn more [in this example](../../campaign-opt/using/filtering-rules.md).

### Avoid attachments

Attachments remain one of the most common vectors for the proliferation of malware, most especially when they are sent in bulk. Include a secure link to the document instead of attaching it. This ensures an additional layer of security to prevent unintended redistribution, and vastly reduces the chances that the message will be rejected at inbound email gateways for message size or security reasons.
