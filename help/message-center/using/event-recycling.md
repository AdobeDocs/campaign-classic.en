---
title: Event recycling
seo-title: Event recycling
description: Event recycling
seo-description: 
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
---

# Event recycling{#event-recycling}

If the delivery of a message on a specific channel fails, Adobe Campaign can resend the message using a different channel. For instance, if a delivery on the SMS channel fails, the message is resent using the email channel.

To do this, you need to configure a workflow which recreates all events with the **Delivery error** status, and assigns a different channel to them.

>[!CAUTION]
>
>This step can only be carried out using a workflow and is therefore reserved for expert users. For more information, please contact Adobe account executive.

