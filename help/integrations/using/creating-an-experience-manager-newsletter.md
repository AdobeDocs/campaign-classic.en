---
title: Creating an Experience Manager newsletter
seo-title: Creating an Experience Manager newsletter
description: Creating an Experience Manager newsletter
seo-description: 
page-status-flag: never-activated
uuid: 392194ed-47e3-4334-93ae-f28f493f802b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
topic-tags: adobe-experience-manager
content-type: reference
discoiquuid: ba3e42af-9654-445a-bada-9b27ec9ecd2f
index: y
internal: n
snippet: y
---

# Creating an Experience Manager newsletter{#creating-an-experience-manager-newsletter}

This integration can be used for example to create a newsletter in Adobe Experience Manager which will then be used in Adobe Campaign as part of an email campaign.

For a more detailed example on how to use this integration, refer to this [step-by-step guide](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html).

**From Adobe Experience Manager:**

1. From your AEM author instance, click the **Adobe Experience** logo in the upper left side of the page and select **Sites**.

   ![](assets/aem_uc_1.png)

1. Select **Campaigns > Name of your brand (here We.Retail) > Master Area > Email campaigns**.
1. Click the **Create** button in the upper right side of the page then select **Page**.

   ![](assets/aem_uc_2.png)

1. Select the **Adobe Campaign Email (AC 6.1)** template and name your newsletter.
1. Once your page is created, access the **Page information** menu and click **Open Properties**.

   ![](assets/aem_uc_3.png)

1. In the **Cloud Services** tab, select **Adobe Campaign** as **Cloud service configuration** and your Adobe Campaign instance in the second drop-down.

   ![](assets/aem_uc_4.png)

1. Edit your email content by adding components, e.g. personalization fields from Adobe Campaign.
1. When your email is ready, access the **Page information** menu and click **Start workflow**.

   ![](assets/aem_uc_5.png)

1. From the first drop-down, select** Publish to Adobe Campaign** as workflow model and click **Start workflow**.

   ![](assets/aem_uc_6.png)

1. Then, as the previous step, launch the **Approve for Campaign** workflow.
1. A disclaimer appears on top of your page. Click **Complete** to confirm the review and click **Ok**.

   ![](assets/aem_uc_7.png)

1. Click again **Complete** and select **Newsletter approval** in the **Next Step** drop-down.

   ![](assets/aem_uc_8.png)

Your newsletter is now ready and synchronized in Adobe Campaign.

**From Adobe Campaign:**

1. From the **Campaigns** tab, click **Deliveries** then **Create**.

   ![](assets/aem_uc_9.png)

1. In the **Delivery template** drop-down, select the **Email delivery with AEM content (mailAEMContent)** template.

   ![](assets/aem_uc_10.png)

1. Add a **Label** to your delivery and click **Continue**.
1. Click the **Synchronize** button.

   If this button does not appear in your interface, click the **Properties** button and select the **Advanced** tab. The **Content editing mode** field should be set to **AEM** with your AEM instance in the **AEM account** field.

   ![](assets/aem_uc_11.png)

1. Select the delivery previously created in Adobe Experience Manager and click **Ok**.
1. Click the **Refresh content** button as soon as some changes are made to your AEM delivery.

   ![](assets/aem_uc_12.png)

Your email is now ready to be send to your audience.
