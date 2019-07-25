---
title: Creating seed addresses
seo-title: Creating seed addresses
description: Creating seed addresses
seo-description: 
page-status-flag: never-activated
uuid: a76b23a3-b9eb-485e-9b88-3271ed5674a8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: b3414ff4-4631-42d8-8248-8c1fba5ba949
index: y
internal: n
snippet: y
---

# Creating seed addresses{#creating-seed-addresses}

Seed addresses are not managed via standard profiles and targets, but in a dedicated node of the Adobe Campaign hierarchy **Resources > Campaign management > Seed addresses**.

You can create sub-folders in order to organize the seed addresses. To do this, right-click the **Seed addresses** node and select **Create a new 'Seed addresses' folder**. Name the sub-folder and then press **Enter** to validate. You can now create or copy seed addresses to this sub-folder. For more on this, refer to [Defining addresses](../../delivery/using/creating-seed-addresses.md#defining-addresses).

Adobe Campaign also lets you create seed address templates which are imported into deliveries or campaigns and adapted based on the specific needs of the concerned deliveries and campaigns. Refer to [Creating seed address templates](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates).

## Defining addresses {#defining-addresses}

To create seed addresses, follow the steps below:

1. Click the **New** button above the list of seed addresses.
1. Enter the data linked to the address in the matching fields from the **Recipient** tab. The available fields correspond to the standard fields in the profiles of the delivery recipients (nms:recipient table): name, first name, email, etc.

   >[!NOTE]
   >
   >The label of the address is automatically filled in with the last name and first name you defined.  
   >It is not necessary to enter all fields of each tab when creating a seed address. Any missing personalization elements are entered randomly during delivery.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. In the **Seed fields** tab, enter the values that will be inserted in the delivery logs during the analysis phase (in the **nms:broadLog** table).
1. In the **Additional data** tab, enter the personalization data used for the deliveries created in the Datamanagement workflows and which you want to assign a specific value to.

## Creating seed address templates {#creating-seed-address-templates}

To create address templates which will be imported and may be modified for each delivery, the process is the same as when defining a new seed address. The only difference is that seed address templates addresses must be stored in a 'Template' type folder.

To define a template folder, apply the following process:

1. Create a new **Seed addresses** type folder, right-click the folder then select **Properties...**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Click the **Restriction** tab and add the following filtering condition: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Addresses stored in this folder may now be used as address templates. You can import them into deliveries or campaigns and adapt them based on the specific needs of the concerned deliveries and campaigns (see [Adding seed addresses](../../delivery/using/adding-seed-addresses.md)).

