---
product: campaign
title: Campaign
description: Campaign
audience: workflow
content-type: reference
topic-tags: technical-workflows
---

# Campaign{#campaign}

The workflows detailed below are installed with the **Campaign** module by default. For more on this module, refer to this [section](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>These workflows MUST be started in order for the campaign processes to be executed at a campaign level.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Cost calculation</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> This workflow starts the calculation of expense and cost lines on the budgets, plans, programs, campaigns, deliveries and tasks.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Orders and alerts</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> This workflow launches stock calculation on the order lines and manages warning alerts thresholds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobs on deliveries in campaigns</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> This workflow triggers the approved deliveries and starts post-processing the service provider for an external delivery. It also sends approval notifications and reminders.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Campaign jobs</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> This workflow manages the jobs for marketing campaigns (launches targeting, file extraction, etc.). It also creates workflows related to recurring and periodic campaigns.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobs on service providers</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> This workflow starts processing the provider (email to the router and post-processing) once deliveries have been approved. <br /> </td> 
  </tr> 
 </tbody> 
</table>

