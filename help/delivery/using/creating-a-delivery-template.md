---
product: campaign
title: Create a delivery template
description: Create a delivery template
feature: Delivery Templates
hide: true
role: User
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
TQID: https://experienceleague.adobe.com/5rlrthjXAnU8yfU1z67u-7uD0Z-pRfm0-Or5q7PBs-Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
---
# Creating a delivery template{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](#delivery-template-video)

## Converting an existing delivery to a template {#converting-an-existing-delivery-to-a-template}

A delivery can be converted to a template for new repeated delivery actions. To convert a delivery to a template, select it from the delivery list, accessible via the **[!UICONTROL Campaign management]** node of the tree.

Right-click and select **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

This action creates a delivery template from the selected delivery. You must enter the folder where it is saved (in the **[!UICONTROL Folder]** field) as well as the folder where the deliveries created based on this template are created (in the **[!UICONTROL Execution folder]** field).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

For more information on the configuration mode, refer to [Linking the template to a delivery](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Creating a new template {#creating-a-new-template}

>[!NOTE]
>
>To avoid configuration errors, Adobe recommends that you duplicate a native template and customize its settings rather than create a new template.

To configure a delivery template, carry out the following steps:

1. Open the Campaign Explorer.
1. In the **Resources** folder, select **Templates** then **Delivery templates**.

   ![](assets/delivery_template_1.png)

1. Click **New** in the toolbar to create a new delivery template, or **Duplicate** an existing template.

   ![](assets/delivery_template_2.png)

1. Modify the **Label** and the **Internal name** of the folder.
1. Save your template and reopen it.
1. Click the **Properties** button, and then modify the values according to your requirements.

   ![](assets/delivery_template_3.png)

1. In the **General** tab, confirm or change the locations selected in the **Execution folder**, **Folder**, and **Routing** drop-down menus.

   ![](assets/delivery_template_4.png)

1. Complete the **Email parameters** category with your email subject and targeted population.
1. Add your **HTML content** to personalize your template, you can display a mirror page link and an unsubscription link.
1. Select the **Preview** tab. In the **Test personalization** drop-down menu, select **Recipient** to preview your template as the chosen profile.

   ![](assets/delivery_template_5.png)

1. Click **Save**. Your template is now ready to be used in a delivery.


## Tutorial videos {#delivery-template-video}

### How to configure a delivery template 

The following video demonstrates how to configure a template for an ad hoc delivery.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### How to set up delivery templates properties

The following video shows how to set the delivery template properties and explains each property in detail.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### How to deploy an ad-hoc delivery template

This video explains how to deploy an ad-hoc email delivery template and it explains the difference between an email delivery and a delivery workflow.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).
