---
product: campaign
title: Interaction
description: Interaction
hide: true
feature: Workflows, Interaction, Offers
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
---

# Interaction{#interaction}



The workflows detailed below are installed with the **Offer engine (Interaction)** add-on by default. 

For more on this, depending on your Campaign version, refer to these sections:
  
![](assets/do-not-localize/v7.jpeg)[  Campaign v7 documentation](../../interaction/using/interaction-and-offer-management.md)
  
![](assets/do-not-localize/v8.png)[  Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Full aggregate calculation (propositionrcp cube)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> This workflow updates the <strong>Full</strong> aggregate for the <strong>Offer proposition</strong> cube. It is triggered every day at 6am by default. This aggregate captures the following dimensions: Channel, Delivery, Marketing Offer and Date.<br /> The <strong>Offer proposition</strong> cube is then used to generate reports based on offers. You can learn more about cubes in <a href="../../reporting/using/ac-cubes.md">this section</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter full aggregate calculation</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> This workflow updates the <strong>Full</strong> aggregate for the <strong>Message center</strong> cube. It is triggered every day at 3am by default. This aggregate captures the following dimensions: Channel, Date, Status and Event type.<br /> The <strong>Message center</strong> cube is then used to generate reports based on events. You can learn more about cubes in <a href="../../reporting/using/ac-cubes.md">this section</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

