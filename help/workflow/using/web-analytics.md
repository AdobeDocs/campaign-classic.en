---
title: Web Analytics
seo-title: Web Analytics
description: Web Analytics
seo-description: 
page-status-flag: never-activated
uuid: 72ef0fca-618b-43d7-b057-e1f87708f85e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: d94a57e8-6e55-47d3-b5a4-4a89e51e973f
index: y
internal: n
snippet: y
---

# Web Analytics{#web-analytics}

The workflows detailed below are installed with the **Web Analytics connectors** module by default. For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Sending of indicators and campaign attributes</strong><br /> </td> 
   <td> <strong>webAnalyticsSendMetrics</strong><br /> </td> 
   <td> This workflow lets you send email campaign indicators from Adobe Campaign to Adobe Experience Cloud Suite via the Adobe® Genesis connector. The indicators concerned are as follows: <strong>Sent</strong> (iSent), <strong>Total count of opens</strong> (iTotalRecipientOpen), <strong>Total number of recipients who clicked</strong> (iTotalRecipientClick), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Identification of converted contacts</strong><br /> </td> 
   <td> <strong>webAnalyticsFindConverted</strong><br /> </td> 
   <td> This workflow indexes site visitors that have completed their purchase after a re-marketing campaign. The data recovered by this workflow can be accessed in the <strong>Re-marketing efficiency report</strong> (Refer to this <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> page</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Event purge</strong><br /> </td> 
   <td> <strong>webAnalyticsPurgeWebEvents</strong><br /> </td> 
   <td> This workflow lets you delete every event from the database field according to the period configured in the <strong>Lifespan</strong> field. <br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Recovery of web events</strong><br /> </td> 
   <td> <strong>webAnalyticsGetWebEvents</strong><br /> </td> 
   <td> Every hour, this workflow downloads segments on internet user behavior on a given site, puts them into the Adobe Campaign database and launches the re-marketing workflow. <br /> </td> 
  </tr> 
 </tbody> 
</table>

