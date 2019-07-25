---
title: Routing towards a template
seo-title: Routing towards a template
description: Routing towards a template
seo-description: 
page-status-flag: never-activated
uuid: b00fd891-27ec-427b-835f-09f854c6728b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 725fad14-3ed4-4170-bb40-90dd495cf7eb
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

