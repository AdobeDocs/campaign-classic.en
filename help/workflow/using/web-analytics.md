---
title: Web Analytics
seo-title: Web Analytics
description: Web Analytics
seo-description: 
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
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
   <td> <span class="uicontrol">Sending of indicators and campaign attributes</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> This workflow lets you send email campaign indicators from Adobe Campaign to Adobe Experience Cloud Suite via the Adobe® Genesis connector. The indicators concerned are as follows: <strong>Sent</strong> (iSent), <strong>Total count of opens</strong> (iTotalRecipientOpen), <strong>Total number of recipients who clicked</strong> (iTotalRecipientClick), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identification of converted contacts</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> This workflow indexes site visitors that have completed their purchase after a re-marketing campaign. The data recovered by this workflow can be accessed in the <span class="uicontrol">Re-marketing efficiency report</span> (Refer to this <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> page</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Event purge</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> This workflow lets you delete every event from the database field according to the period configured in the <span class="uicontrol">Lifespan</span> field. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recovery of web events</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Every hour, this workflow downloads segments on internet user behavior on a given site, puts them into the Adobe Campaign database and launches the re-marketing workflow. <br /> </td> 
  </tr> 
 </tbody> 
</table>

