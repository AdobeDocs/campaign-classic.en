---
title: Creating offer categories
seo-title: Creating offer categories
description: Creating offer categories
seo-description: 
page-status-flag: never-activated
uuid: e9eadc5a-54aa-49be-9f20-f676671be1c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
discoiquuid: 09d0b6aa-2af8-4059-9e57-7cdb0b1c87b6
index: y
internal: n
snippet: y
---

# Creating offer categories{#creating-offer-categories}

The creation of offer categories can only take place in the **Design** environment. They are deployed automatically in the **Live** environment (i.e. made available) when the created/modified offer(s) they contain are approved. By default, the **Design** environment contains a category to receive all offers. Sub-categories can be created to add hierarchy to the catalog offers.

For each category, you can define eligibility dates, i.e. a period beyond which the offers contained in the category may no longer be presented to their target. If you want the offers from a specific category to be selected as a priority by the offer engine, to better expose a product for example, you can increase their weights for a given period by adding a multiplying weight to the category.

To create an additional category, apply the following steps:

1. Go to the **Offer catalog** folder.

   ![](assets/offer_cat_create_001.png)

1. Right click and select **Create a new "Offer category" folder** from the drop-down list.

   ![](assets/offer_cat_create_002.png)

1. Re-name the category. You can edit the label later using the **General** tab.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Repeat these steps to create as many categories as necessary.

   Thereafter, as needed you can:

    * assign eligibility dates from the **Eligibility** tab.
    
      ![](assets/offer_cat_create_004.png)

    * enter key words that may be used to select offers from within this category, using the **Themes** field.
    
      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >When calling up the offer engine, only the part of the catalog in which the themes or categories match the parameters is selected.

    * You can temporarily "boost" the offer weight of a category for a given period via the **Multiplier weight** field.
    
      ![](assets/offer_cat_create_006.png)

A recap of the eligibility rules is available on the dashboard of the offers included in the category. To view them, click the **Schedule and eligibility rules of the offer** link.

![](assets/offer_create_006.png)

