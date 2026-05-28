---
product: campaign
title: Implementation steps
description: Implementation steps for Campaign Interaction module
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
TQID: https://experienceleague.adobe.com/tyQuMLnpH7JPcMah758d4YyG7Kd9ACKQLsMNiWvpOtY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management (Campaign)
subfeature_v2: []
---
# Implementation steps{#implementation-steps}



## Configuring Interaction {#configuring-interaction}

>[!NOTE]
>
>The following steps should be performed by an **Administrator** profile and only in design environments.

1. Creating user profiles. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. Creating an offer environment by targeting dimension. For more on this, refer to [Creating an offer environment](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Creating typology rules for each environment. For more on this, refer to [Creating and referencing an offer presentation rule](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Creating offer spaces for each environment and configuring rendering functions. For more on this, refer to [Creating offer spaces](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >If the space is defined by a unitary channel on identified mode, you must specify the advanced parameters for this space.

1. Configuring the offer engine for inbound interactions in order to present and update one or several offers.

   The various integration modes are detailed in [About inbound channels](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >When a space is created on the inbound Web channel, a configuration is also necessary on the site on which the offer will be displayed.

## Managing the offer catalog {#managing-the-offer-catalog-}

>[!NOTE]
>
>The following steps should be carried out by an **Offer manager**.

1. Creating offer categories in design environments. For more on this, refer to [Creating offer categories](../../interaction/using/creating-offer-categories.md).
1. Creating offers in design environments. For more on this, refer to [Creating an offer](../../interaction/using/creating-an-offer.md).
1. Approving and publishing offers on one or several spaces in order to make them available on live environments for the delivery manager. For more on this, refer to [Approving and activating an offer](../../interaction/using/approving-and-activating-an-offer.md).

## Using the offer catalog {#using-the-offer-catalog-}

>[!NOTE]
>
>The following steps should be performed by a **Delivery manager** profile. They can only edit offers in live environments.

1. Creating a campaign.
1. Referencing an offer in a campaign or a campaign delivery. For more on this, refer to [About outbound channels](../../interaction/using/about-outbound-channels.md).
