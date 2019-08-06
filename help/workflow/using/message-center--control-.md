---
title: Message Center (Control)
seo-title: Message Center (Control)
description: Message Center (Control)
seo-description: 
page-status-flag: never-activated
uuid: de7ea16d-38d9-45b9-8491-662add42c46a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 25610ec7-9c73-4c79-8148-8bac4cf5d14e
index: y
internal: n
snippet: y
---

# Message Center (Control){#message-center-control}

The workflow detailed below is scheduled to run every hour. It is installed with the **Message Center - Control** module by default. For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

To know more about how to configure technical workflows related to the Message Center module, refer to [this page](../../message-center/using/technical-workflows.md). 

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Message Center &lt;external_account_name&gt;</strong><br /> </td> 
   <td> <strong>mcSynch_</strong></td> 
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

