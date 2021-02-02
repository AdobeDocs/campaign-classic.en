---
solution: Campaign Classic
product: campaign
title: Coonfiguring A/B testing
description: Learn how to configure A/B testing in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
---

# Configuring A/B testing {#configuring-a-b-testing}

A/B testing is implemented using Campaign Classic workflows. To do this:

1. Target the desired population.
1. Split the population into sub-sets on which you will test the variants of your delivery.

     For example, you can send one version of a delivery to a small portion of the targeted population, and another version to the remaining population. This allows you to test a new version of a delivery as opposed to the delivery that is usually sent to your customers. You can also divide the targeted population into 3 groups in order to send them  three different versions of a delivery.

1. Create one version of the delivery for each sub-set. The variant to test can be the subject, the message content, sender name, etc.
1. Start the workflow, then use the delivery logs to analyze the behaviour of the sub-sets with each variant.

>[!NOTE]
>
>You can also set up a workflow in order to test different variants of a delivery on several population samples, and then automatically send the most successfull version of a delivery to the remaining population after a specific amount of time. For more on this, refer to the dedicated use case.

The steps to configure the workflow are as follows:

1. Create a new workflow then configure a **[!UICONTROL Query]** activity to target the desired population.
1. Add a **[!UICONTROL Split]** activity to divide the targeted population into multiple sub-sets.
1. Open the activity, then configure each sub-set according to your needs.

    In this example, we want to test 2 new subjects for a newsletter by sending each of them to 10% of the targeted population. For more on how to configure a **[!UICONTROL Split]** activity, refer to this section.

   ![](assets/ab-testing-split.png)

1. Add a transition in order to send to the remaining population the newsletter with the current subject.

   ![](assets/ab-testing-complement.png)

1. For each sub-set, add the corresponding version of the delivery.

   ![](assets/ab-testing-delivery.png)

You can now start the workflow. Once the deliveries have been sent, you will be able to track the behaviour of the three sub-sets in the delivery logs, in order to see which subject has been the most successfull.

In the email dashboard, several indicators are available to help you measure your A/B test: number of clicks, opens, bounces, and so on.
