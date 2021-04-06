---
solution: Campaign Classic
product: campaign
title: Creating offer categories
description: Creating offer categories
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
---
# Creating offer categories{#creating-offer-categories}

The creation of offer categories can only take place in the **[!UICONTROL Design]** environment. They are deployed automatically in the **[!UICONTROL Live]** environment (i.e. made available) when the created/modified offer(s) they contain are approved. By default, the **[!UICONTROL Design]** environment contains a category to receive all offers. Sub-categories can be created to add hierarchy to the catalog offers.

For each category, you can define eligibility dates, i.e. a period beyond which the offers contained in the category may no longer be presented to their target. If you want the offers from a specific category to be selected as a priority by the offer engine, to better expose a product for example, you can increase their weights for a given period by adding a multiplying weight to the category.

To create an additional category, apply the following steps:

1. Go to the **[!UICONTROL Offer catalog]** folder.

   ![](assets/offer_cat_create_001.png)

1. Right click and select **[!UICONTROL Create a new "Offer category" folder]** from the drop-down list.

   ![](assets/offer_cat_create_002.png)

1. Re-name the category. You can edit the label later using the **[!UICONTROL General]** tab.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Repeat these steps to create as many categories as necessary.

   Thereafter, as needed you can:

    * Assign eligibility dates from the **[!UICONTROL Eligibility]** tab.
    
      ![](assets/offer_cat_create_004.png)

    * Enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.
    
      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >When calling up the offer engine, only the part of the catalog in which the themes or categories match the parameters is selected.

    * Temporarily "boost" the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.
    
      ![](assets/offer_cat_create_006.png)

A recap of the eligibility rules is available on the dashboard of the offers included in the category. To view them, click the **[!UICONTROL Schedule and eligibility rules of the offer]** link.

![](assets/offer_create_006.png)
