---
product: campaign
title: Define the final delivery
description: Learn how to perform A/B testing through a dedicated use case
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
TQID: https://experienceleague.adobe.com/P0oI4PhLZB-iBFDrEJ2Qy7eIOPYWSWYu5s6j3yCN6j0
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
# AB testing: Define the final delivery {#step-6--defining-the-final-delivery}

Once the script is created to select the A/B test winner, you can define the parameters of the final delivery.

1. Connect the **[!UICONTROL JavaScript code]** activity to the remaining **[!UICONTROL Delivery]** activity.
1. Open the **[!UICONTROL Delivery]** activity.
1. Uncheck the **[!UICONTROL Generate an outbound transition]** option to finish the workflow with this activity.
1. Leave the other options to their default values. 

   ![](assets/ab_test_final_delivery.png)

By preparing the delivery specified in the transition (defined via the **[!UICONTROL Javascript Code]** activity), you will be then able to approve it and to start the sending, as described in the next step.

You can now start the workflow. [Learn more](a-b-testing-uc-start-workflow.md).
