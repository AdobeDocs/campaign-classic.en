---
title: Operator profiles
seo-title: Operator profiles
description: Operator profiles
seo-description: 
page-status-flag: never-activated
uuid: d3b458f0-2118-4563-8a20-e4fb35d21798
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
discoiquuid: da645b87-cfda-4892-9e70-8c0682bc89d0
index: y
internal: n
snippet: y
---

# Operator profiles{#operator-profiles}

There are two types of operators who use Interaction: offer managers and delivery managers. They each have specific rights that only give them access to some parts of the tree and the platform.

* **Offer manager**: creates and maintains offers
* **Delivery manager**: approves and uses offers

The steps for creating operators specific to Interaction are identical to those used to create all other operators on the platform. For more on this, refer to [this section](../../platform/using/access-management.md#creating-an-operator). The rights are configured during operator creation.

## Offer manager {#offer-manager}

1. Create a new operator.
1. Go to the **Groups and named rights** window, click **Add** and select the **Offer manager** group.

   ![](assets/offer_operators_create_001.png)

The rights assigned to the offer manager enable them to carry out the following tasks:

* Modify **Design** environments.
* View **Live** environments.
* Configure administration functions (predefined spaces and filters).
* Create and alter categories.
* Create offers.
* Configure offer eligibility.
* Approve offers.

  >[!NOTE]
  >
  >The offer manager can only approve an offer in two certain cases. The first being if nobody in particular was specified as the reviewer, and the second being if the operator in charge of creating templates (with the right to assign reviewers) specified him/her as the reviewer in the offer template on which the offer was based.

## Delivery manager {#delivery-manager}

1. Create a new operator.
1. Go to the **Groups and named rights** window, click **Add** and select the **Delivery manager** group.

   ![](assets/offer_operators_create_002.png)

The rights assigned to the delivery manager are/enable them to carry out the following tasks:

* Display **Live** environments.
* Display and modify offer categories.
* Approve offers if s/he is specified as one of its reviewers.

  >[!NOTE]
  >
  >The delivery manager can only approve an offer if he has been defined as a reviewer during the offer configuration.

## Recap of rights according to operator {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Offer manager (editing)</strong><br /> </td> 
   <td> <strong>Offer manager (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Tree structure level</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offers being edited / Live offers<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Recipient - Environment<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Spaces<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Predefined offer filters<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Typology<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Typology rules<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Offer catalog<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Offer category<br /> </td> 
   <td> Read / Write<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Delivery manager (editing)</strong><br /> </td> 
   <td> <strong>Delivery manager (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Tree structure level</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offers being edited / Live offers<br /> </td> 
   <td> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Recipient - Environment<br /> </td> 
   <td> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Spaces<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Predefined offer filters<br /> </td> 
   <td> Read<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Typology<br /> </td> 
   <td> Read<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Typology rules<br /> </td> 
   <td> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Offer catalog<br /> </td> 
   <td> Read<br /> </td> 
   <td> Read<br /> </td> 
  </tr> 
  <tr> 
   <td> Offer category<br /> </td> 
   <td> </td> 
   <td> Read<br /> </td> 
  </tr> 
 </tbody> 
</table>

