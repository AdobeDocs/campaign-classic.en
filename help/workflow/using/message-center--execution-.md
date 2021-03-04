---
solution: Campaign Classic
product: campaign
title: Message Center (Execution)
description: Message Center (Execution)
audience: workflow
content-type: reference
topic-tags: technical-workflows
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
   <td> <span class="uicontrol">Update event status</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
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
   <td> <span class="uicontrol">Processing batch events</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> This workflow lets you put batch events into a queue before associating them with a message template. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processing real time events</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> This workflow lets you put real-time events into a queue before associating them with a message template. <br /> </td> 
  </tr> 
 </tbody> 
</table>

