---
product: campaign
title: Configure A/B testing
description: Learn how to configure A/B testing in Campaign
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
TQID: https://experienceleague.adobe.com/PHIsuJZ-o5mBRAPggyVYdzS7PBXL9GYCBc6Fr56ur5Q
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
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
---
# Configure A/B testing {#configuring-a-b-testing}

This section details how to build a workflow to perform A/B testing. 

1. Create a new workflow then configure a Query activity to target the desired population. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}.

1. Add a Split activity to divide the targeted population into multiple sub-sets. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}.

1. Open the activity, then configure each sub-set according to your needs. For more on how to configure a **[!UICONTROL Split]** activity, refer to [this section](../../workflow/using/split.md).

    In this example, we want to test 2 new subjects for a newsletter by presenting each of them to 10% of the targeted population.

   ![](assets/ab-testing-split.png)

1. Add a transition in order to send to the remaining population the newsletter with the current subject. To do this, activate the **[!UICONTROL Generate complement]** option from the **[!UICONTROL General]** tab.

   ![](assets/ab-testing-complement.png)

1. For each sub-set, add the version of the delivery to test.

   ![](assets/ab-testing-delivery.png)

You can now start the workflow. Once the deliveries have been sent, you will be able to track the behavior of the three sub-sets in the delivery logs, in order to see which subject has been the most successful.

Workflows also allow you to automate your processes by automatically identifying the delivery variant that performed better, then sending it to the remaining population. For more on this, refer to this dedicated [use case](a-b-testing-use-case.md).
