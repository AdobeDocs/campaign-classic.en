---
title: Interaction
seo-title: Interaction
description: Interaction
seo-description: 
page-status-flag: never-activated
uuid: d0e4a887-edd9-408d-8148-2143b00afbd8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 60bbe2e7-fe0c-4e24-9b6b-fefdeb6409c2
index: y
internal: n
snippet: y
---

# Interaction{#interaction}

The workflow detailed below is installed with the **Offer engine (Interaction)** module by default. For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Full aggregate calculation (propositionrcp cube)</strong><br /> </td> 
   <td> <strong>agg_nmspropositionrcp_full</strong><br /> </td> 
   <td> This workflow updates the <strong>Full</strong> aggregate for the <strong>Offer proposition</strong> cube. It is triggered every day at 6am by default. This aggregate captures the following dimensions: Channel, Delivery, Marketing Offer and Date.<br /> The <strong>Offer proposition</strong> cube is then used to generate reports based on offers. You can learn more about cubes in <a href="../../reporting/using/about-cubes.md">this section</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

