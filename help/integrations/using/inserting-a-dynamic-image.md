---
product: campaign
title: Insert a dynamic image
description: Insert a dynamic image
feature: Target Integration
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
---
# Insert Target dynamic content {#inserting-a-dynamic-image}

 

In this page, learn how to integrate a dynamic offer from Adobe Target into an email in Adobe Campaign.

The aim is to create a delivery with an image block which dynamically changes according to the recipient's country: the data is sent with each mbox request and depends on the recipient's IP address.

In this message, images can vary dynamically according to the following user-experiences:

* The email is opened in France.
* The email is opened in the United States.
* If none of these conditions apply, a default image is displayed.

![](assets/target_4.png)

To perform this, apply the following steps:

1. [Insert the dynamic offer in an email](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Create redirect offers](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Create audiences](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Create an Experience Targeting Activity](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Preview and send the email](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Insert the dynamic offer in an email {#inserting-dynamic-offer}

In Adobe Campaign, once you're done defining the target and content of your email, you can insert a dynamic image from Target.

To do this, specify the default image's URL, the location name, and the fields you want to transfer to Target.

In Adobe Campaign, there are two ways to insert a dynamic image from Target into an email:

* If you are using the digital content editor, choose an existing image and select **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** from the toolbar.

   ![](assets/target_5.png)

* If you are using the standard editor, place the cursor where you want to insert the image and select **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** from the personalization drop-down menu.

   ![](assets/target_12.png)

### Define the image parameters {#defining-image-parameters}

* The **[!UICONTROL Default image]**'s URL: The image that will be displayed when none of the conditions are fulfilled. You can also select an image from your Assets library.
* The **[!UICONTROL Target location]**: Enter a name for your dynamic offer's location. You will have to select this location in your Target activity.
* The **[!UICONTROL Landing Page]**: If you want the default image to redirect to a default landing page. This URL is only for the cases when the default image is displayed in the final email and is optional.
* The **[!UICONTROL Additional decision parameters]**: Specify the mapping between the fields defined in the Adobe Target segments and the Adobe Campaign fields. The Adobe Campaign fields used must have been specified in the rawbox. In our example, we added the Country field.

If you use Enterprise permissions in your settings in Adobe Target, add the corresponding property in this field. Learn more about Target Enterprise permissions in [this page](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html).

![](assets/target_13.png)

## Create redirect offers {#create-redirect-offers}

In Target, you can create different versions of your offer. Depending on each user experience, a redirect offer can be created and you can specify the image that will be displayed.

In our case, we need two redirect offers, the third one (the default one) is to be defined in Adobe Campaign.

1. To create a new redirect offer in Target Standard, from the **[!UICONTROL Content]** tab, click **[!UICONTROL Code offers]**.

1. Click **[!UICONTROL Create]** then **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Enter a name for the offer and the URL of your image.

   ![](assets/target_6.png)

1. Follow the same procedure for the remaining redirect offer. For more on this, refer to this [page](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html).

## Create audiences {#audiences-target}

In Target, you need to create the two audiences into which the people who visit your offer will be categorized for the different contents to be delivered. For each audience, add a rule to define who will be able to see the offer.

1. To create a new audience in Target, from the **[!UICONTROL Audiences]** tab, click **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Add a name to your audience.

   ![](assets/audiences_2.png)

1. Click **[!UICONTROL Add a rule]** and select a category. The rule uses specific criteria to target the visitors. You can refine the rules by adding conditions or by creating new rules in other categories.

1. Follow the same procedure for the remaining audiences.

## Create an Experience Targeting Activity {#creating-targeting-activity}

In Target, we need to create an Experience Targeting activity, define the different experiences, and associate them with the corresponding offers.

### Define the audience {#defining-the-audience}

1. To create an Experience Targeting activity, from the **[!UICONTROL Activities]** tab, click **[!UICONTROL Create Activity]** then **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. Select **[!UICONTROL Form]** as **[!UICONTROL Experience Composer]**.

1. Choose an audience by clicking the **[!UICONTROL Change audience]** button.

   ![](assets/target_10_2.png)

1. Select the audience that was created in the previous steps.

   ![](assets/target_10_3.png)

1. Create another experience by clicking **[!UICONTROL Add Experience Targeting]**.

### Define the location and content {#defining-location-content}

Add a content for each audience:

1. Select the location name that you chose when inserting the dynamic offer in Adobe Campaign.

   ![](assets/target_15.png)

1. Click the drop-down button and select **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Select the redirect offer that you had previously created.

   ![](assets/target_content_2.png)

1. Follow the same steps for the second experience.

### Define the activity {#defining-activity}

The **[!UICONTROL Target]** window summarizes your activity. If necessary, you can add other experiences.

   ![](assets/target_experience.png)

The **[!UICONTROL Goal & Settings]** window allows you to personalize your activity by setting a priority, an objective, or a duration.

The **[!UICONTROL Reporting Settings]** section lets you select an action and edit the parameters that will determine when your goal is achieved.

   ![](assets/target_experience_2.png)

## Preview and send the email {#preview-send-email}

In Adobe Campaign, you can now preview your email and test its rendering on different recipients. You will notice that the image changes according to the different experiences created. To learn more on email creation, refer to this [page](../../delivery/using/defining-the-email-content.md).

You are now ready to send your email including a dynamic offer from Target.

   ![](assets/target_20.png)
