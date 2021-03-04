---
solution: Campaign Classic
product: campaign
title: Interaction
description: Interaction
audience: workflow
content-type: reference
topic-tags: technical-workflows
---

# Interaction{#interaction}

The workflows detailed below are installed with the **Offer engine (Interaction)** module by default. For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

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
   <td> This workflow updates the <strong>Full</strong> aggregate for the <strong>Offer proposition</strong> cube. It is triggered every day at 6am by default. This aggregate captures the following dimensions: Channel, Delivery, Marketing Offer and Date.<br /> The <strong>Offer proposition</strong> cube is then used to generate reports based on offers. You can learn more about cubes in <a href="../../reporting/using/about-cubes.md">this section</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter full aggregate calculation</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> This workflow updates the <strong>Full</strong> aggregate for the <strong>Message center</strong> cube. It is triggered every day at 3am by default. This aggregate captures the following dimensions: Channel, Date, Status and Event type.<br /> The <strong>Message center</strong> cube is then used to generate reports based on events. You can learn more about cubes in <a href="../../reporting/using/about-cubes.md">this section</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

