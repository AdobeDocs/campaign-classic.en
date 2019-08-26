---
title: Routing towards a template
seo-title: Routing towards a template
description: Routing towards a template
seo-description: 
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
index: y
internal: n
snippet: y
---

# Routing towards a template{#routing-towards-a-template}

Once the message template is published on the execution instance(s), two templates to be linked to a real time or a batch event are automatically generated. The routing step consists of linking an event to the appropriate message template. Linking is based on the event type specified in the properties of the event itself and those of the template.

Definition of the event type in the event properties:

![](assets/messagecenter_event_type_001.png)

Definition of the event type in the message template properties:

![](assets/messagecenter_event_type_002.png)

By default, routing is based on the following information:

* the event type,
* the channel to be used (by default: email),
* the most recent delivery template, based on the publication date.

