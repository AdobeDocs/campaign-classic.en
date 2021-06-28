---
product: campaign
title: Message Center (Control)
description: Message Center (Control)
audience: workflow
content-type: reference
topic-tags: technical-workflows
---

# Message Center (Control){#message-center-control}

The workflow detailed below is scheduled to run every hour. It is installed with the **Message Center - Control** module by default. 


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
   <td> Message Center &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> This workflow:<br /> 
    <ul> 
     <li> <p>recovers the list of events processed by the operation(s).</p> </li> 
     <li> <p>synchronizes with the NmsBroadLogMsg table in order to recover delivery message qualifications.</p> </li> 
     <li> <p>recovers event delivery logs as soon as synchronization with the NmsBroadLogMsg table has been completed.</p> </li> 
     <li> <p>synchronizes with the NmsTrackingUrl table in order to recover the tracking for delivery URLs.</p> </li> 
     <li> <p>recovers event tracking URLs as soon as synchronization with the NmsTrackingUrl table has been completed.</p> </li> 
     <li> <p>lets you recover all email addresses placed in quarantine every three hours after a delivery has been sent.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

