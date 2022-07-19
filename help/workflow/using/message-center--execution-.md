---
product: campaign
title: Message Center (Execution)
description: Message Center (Execution)
feature: Workflows
---

# Message Center (Execution){#message-center-execution}

![](../../assets/v7-only.svg)

The workflows detailed below are installed with the **Message Center - Execution** add-on by default. 

For more on this, depending on your Campaign version, refer to these sections:
  
![](assets/do-not-localize/v7.jpeg)[  Campaign v7 documentation](../../message-center/using/about-transactional-messaging.md)
  
![](assets/do-not-localize/v8.png)[  Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)

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

