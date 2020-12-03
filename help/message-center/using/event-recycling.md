---
solution: Campaign Classic
product: campaign
title: Event recycling
description: Event recycling
audience: message-center
content-type: reference
topic-tags: event-processing
---

# Event recycling{#event-recycling}

If the delivery of a message on a specific channel fails, Adobe Campaign can resend the message using a different channel. For instance, if a delivery on the SMS channel fails, the message is resent using the email channel.

To do this, you need to configure a workflow which recreates all events with the **Delivery error** status, and assigns a different channel to them.

>[!CAUTION]
>
>This step can only be carried out using a workflow and is therefore reserved for expert users. For more information, please contact Adobe account executive.

