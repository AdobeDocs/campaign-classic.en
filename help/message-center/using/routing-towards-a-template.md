---
title: Routing towards a template
seo-title: Routing towards a template
description: Routing towards a template
seo-description: 
page-status-flag: never-activated
uuid: 8283b13e-2c1c-4312-a12a-e9a54039b616
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 52dac4dd-3e5b-4188-8298-5d200e88a19c
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

