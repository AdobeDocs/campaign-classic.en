---
title: Message Center (Control)
seo-title: Message Center (Control)
description: Message Center (Control)
seo-description: 
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
index: y
internal: n
snippet: y
---

# Message Center (Control){#message-center-control}

The workflow detailed below is scheduled to run every hour. It is installed with the **Message Center - Control** module by default. For more on this module, refer to this [section](https://helpx.adobe.com/campaign/classic/message-center/using/about-transactional-messaging.html).

To know more about how to configure technical workflows related to the Message Center module, refer to [this page](https://helpx.adobe.com/campaign/classic/message-center/using/technical-workflows.html). 

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Message Center 
     <external_account_name /></strong><br /> </td> 
   <td> <strong>mcSynch_
     <external_account_name /></strong>&gt;<br /> </td> 
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

