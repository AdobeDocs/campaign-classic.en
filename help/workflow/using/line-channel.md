---
product: campaign
title: LINE Channel
description: LINE Channel
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
---

# LINE Channel{#line-channel}



The workflows detailed below are installed with the **LINE channel** module by default. For more on this module, refer to this [section](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2 access token update</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> This workflow refreshes the access token to LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Delete blocked LINE users</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> This workflow ensures that the LINE V2 users' data is deleted after they have blocked the LINE official account for 180 days.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID to LineUserID migration</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> This workflow generates the LINE V2 users' ID for migration from LINE V1 to LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

