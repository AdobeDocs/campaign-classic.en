---
title: Inserting a dynamic image
seo-title: Inserting a dynamic image
description: Inserting a dynamic image
seo-description: 
page-status-flag: never-activated
uuid: 610b712b-64c3-4c73-9b5b-4e0f1e5c6474
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 5f277be5-f35d-4a1f-8e46-83651de8d421
index: y
internal: n
snippet: y
---

# Inserting a dynamic image{#inserting-a-dynamic-image}

This section details the steps to carry out in Adobe Campaign to integrate an image from Adobe Target into an email.

You must carry out the following actions in Adobe Target beforehand:

* Create one or several [redirection offers](https://marketing.adobe.com/resources/help/en_US/tnt/help/t_Creating_a_Redirect_Offer.html), in which you must specify the URL of the image you will be using.
* Create one or several [audiences](https://marketing.adobe.com/resources/help/en_US/target/target/t_create-audience.html), to define the target of your activity.
* Create an [Form-based experience composer](https://marketing.adobe.com/resources/help/en_US/tnt/help/t_Creating_an_A_B_Test.html) activity, in which you must select a rawbox and specify several experiences, depending on the number of redirection offers created. For each experience, you must select one of the redirection offers created.

  To specify these experiences, you can create segments using information from Adobe Campaign. To use data from Adobe Campaign in the offer's selection rules, you must specify the data in the rawbox in Adobe Target.

To insert an Adobe Target image in an Adobe Campaign delivery:

1. Create an email delivery.
1. In the available personalization fields, select **Include > Dynamic image served by Adobe Target**.

   ![](assets/tar_insert_dynamic_image.png)

1. In the window that opens, select the image that will appear by default in the email. You can specify the image URL or use a [shared image](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).
1. Enter the name of the rawbox specified in Adobe Target.
1. Enter a URL in the **Landing Page** field if you want the default image to redirect to a default landing page. This URL is only for the cases when the default image is displayed in the final email and is optional.
1. If you use Enterprise permissions in your settings in Adobe Target, add the corresponding property in this field. Learn more about Target Enterprise permissions in [this page](https://marketing.adobe.com/resources/help/en_US/target/target/properties-overview.html). This field is optional and not required if you don't use Enterprise permissions in Target.
1. In **Additional decision parameters**, specify the mapping between the fields defined in the Adobe Target segments and the Adobe Campaign fields. The Adobe Campaign fields used must have been specified in the rawbox.

   ![](assets/tar_additional_decisionning_parameters.png)

   Defining a parameter in Adobe Target is carried out via the rawbox created when integrating the Target image in Adobe Campaign and the **Refinements** option.

   ![](assets/tar_additional_decisionning_parameters_1.png)

   The example shown here demonstrates how to define different experiences for men and women.

You can also define several cases based on the user's email domain and address. The data is automatically recovered from the user's browser when the email is opened.

![](assets/tar_additional_decisionning_parameters_2.png)

When previewing your email, you can see, when selecting different profiles, that the image inserted changes depending on the parameters specified in the Adobe Target activity and in Adobe Campaign.

You can measure the results of your sends in Adobe Target.

![](assets/tar_measure_results.png)

