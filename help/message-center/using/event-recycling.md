---
title: Event recycling
seo-title: Event recycling
description: Event recycling
seo-description: 
page-status-flag: never-activated
uuid: 8e9ff213-65b3-4124-8895-d26bd04bc971
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 87bffa85-15cf-402e-af4b-aaf00acaf958
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

