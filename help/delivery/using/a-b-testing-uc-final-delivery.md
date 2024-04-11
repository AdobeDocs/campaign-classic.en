---
product: campaign
title: Define the final delivery
description: Learn how to perform A/B testing through a dedicated use case
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
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
