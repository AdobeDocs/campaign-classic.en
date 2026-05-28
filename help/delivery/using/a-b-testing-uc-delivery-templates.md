---
product: campaign
title: Create the delivery templates
description: Learn how to perform A/B testing through a dedicated use case
role: User
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
TQID: https://experienceleague.adobe.com/eble-fTf8Rk7fFGnKNh5pLUhMaLdZlJrG-vjrhbHx1I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: e739ee2b-6228-412e-878f-45de0791417d
    internal-label: Use cases
---
# AB testing: Create the delivery templates {#step-3--creating-two-delivery-templates}

We now want to create two delivery templates. Each template will be referenced in an **[!UICONTROL Email delivery]** activity linked to the **[!UICONTROL Split]** activity. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}.

1. Browse to the **[!UICONTROL Resources > Delivery template]** folder.
1. Duplicate the **[!UICONTROL Email]** delivery template.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Create the content to be used for delivery A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repeat this process to create a template for delivery B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

You can now configure the deliveries in the workflow. [Learn more](a-b-testing-uc-configuring-deliveries.md).
