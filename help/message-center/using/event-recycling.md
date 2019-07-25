---
title: Event recycling
seo-title: Event recycling
description: Event recycling
seo-description: 
page-status-flag: never-activated
uuid: 5bc01670-7b98-4d6f-bdca-b4c9f9128e7e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 02d4fede-a65d-4924-8cfb-e7e328e734cb
index: y
internal: n
snippet: y
---

# Event recycling{#event-recycling}

If the delivery of a message on a specific channel fails, Adobe Campaign can resend the message using a different channel. For instance, if a delivery on the SMS channel fails, the message is resent using the email channel.

To do this, you need to configure a workflow which recreates all events with the **Delivery error** status, and assigns a different channel to them.

>[!CAUTION]
>
>This step can only be carried out using a workflow and is therefore reserved for expert users. For more information, please contact Adobe account executive.

