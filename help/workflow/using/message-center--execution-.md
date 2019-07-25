---
title: Message Center (Execution)
seo-title: Message Center (Execution)
description: Message Center (Execution)
seo-description: 
page-status-flag: never-activated
uuid: a959f78b-f2fd-41df-a479-11c8da8fb7d8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 6f3b614b-9b5f-464e-9aa3-f5309aa8178a
index: y
internal: n
snippet: y
---

# Message Center (Execution){#message-center-execution}

The workflows detailed below are installed with the **Message Center - Execution** module by default. For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

To know more about how to configure technical workflows related to the Message Center module, refer to [this page](../../message-center/using/technical-workflows.md). 

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Update event status</strong><br /> </td> 
   <td> <strong>updateEventsStatus</strong><br /> </td> 
   <td> This workflow lets you assign a status to an event. Event statuses are as follows:<br /> 
    <ul> 
     <li> <p><strong>Pending</strong>: the event is in a queue. No message template has yet been associated to it.</p> </li> 
     <li> <p><strong>Pending delivery</strong>: the event is in a queue, a message template has been associated to it and is currently being processed by the delivery.</p> </li> 
     <li> <p><strong>Sent</strong>: this status is copied from the delivery logs. It means that the delivery has been sent.</p> </li> 
     <li> <p><strong>Ignored by the delivery</strong>: this status is copied from the delivery logs. It means that the delivery has been ignored.</p> </li> 
     <li> <p><strong>Delivery error</strong>: this status is copied from the delivery logs. It means that the delivery has failed.</p> </li> 
     <li> <p><strong>Event not covered</strong>: the event has failed to be associated with a message template. The event will not be reprocessed.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <strong>Processing batch events</strong><br /> </td> 
   <td> <strong>batchEventsProcessing</strong><br /> </td> 
   <td> This workflow lets you put batch events into a queue before associating them with a message template. <br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Processing real time events</strong><br /> </td> 
   <td> <strong>rtEventsProcessing</strong><br /> </td> 
   <td> This workflow lets you put real-time events into a queue before associating them with a message template. <br /> </td> 
  </tr> 
 </tbody> 
</table>

