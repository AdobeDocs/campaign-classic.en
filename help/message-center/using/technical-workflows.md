---
title: Technical workflows
seo-title: Technical workflows
description: Technical workflows
seo-description: 
page-status-flag: never-activated
uuid: 338689ad-082b-40e9-a0fa-a79ce6f9689f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 7e1d5522-c05c-498a-96fc-581cf88d11d0
index: y
internal: n
snippet: y
---

# Technical workflows{#technical-workflows}

You must ensure that the technical workflows on the control instance and the different execution instances have indeed been created and started before deploying any transactional message templates.

The various technical workflows related to transactional messaging (Message Center) are broken down between the control instance and the execution instance(s).

## Control instance workflows {#control-instance-workflows}

On the control instance, you must create one archiving workflow per execution instance. The archiving workflows can then be accessed from the **Administration > Production > Message Center** folder. Once created, the archiving workflows are automatically started.

**Distributed architecture**

If you have one or several execution instances registered, on the control instance, you must create one archiving workflow for each **Message Center execution instance** external account. Click the **Create the archiving workflow** button to create and start the workflow.

![](assets/messagecenter_archiving_002.png)

**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **Create the archiving workflow** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)

## Execution instance workflows {#execution-instance-workflows}

On the execution instance(s), the technical workflows for transactional messaging can be accessed from the **Administration > Production > Message Center** folder. You just have to start them. The workflows in the list are:

* **Processing batch events** (internal name: **batchEventsProcessing**): this workflow lets you break down batch events in a queue before they are linked to a message template.
* **Processing real time events** (internal name: **rtEventsProcessing**): this workflow lets you break down real time events in a queue before they are linked to a message template.
* **Update event status** (internal name: **updateEventStatus**): this workflow lets you attribute a status to the event.

  The following event statuses are available:

    * **Pending**: the event is in the queue. No message template has been assigned to it yet.
    * **Pending delivery**: the event is in the queue, a message template has been assigned to it and it is being processed by the delivery.
    * **Sent**: this status is copied from the delivery logs. It means that the delivery has been sent.
    * **Ignored by the delivery**: this status is copied from the delivery logs. It means that the delivery was ignored.
    * **Delivery failed**: this status is copied from the delivery logs. It means that the delivery failed.
    * **Event not taken into account**: the event could not be linked to a message template. The event will not be processed.

