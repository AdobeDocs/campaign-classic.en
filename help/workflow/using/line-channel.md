---
product: campaign
title: LINE Channel
description: LINE Channel
hide: true
feature: Workflows
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: Workflow HeatMap (Campaign)
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities (Campaign)
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities (Campaign)
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

