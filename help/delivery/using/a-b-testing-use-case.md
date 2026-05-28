---
product: campaign
title: AB testing use case
description: Learn how to perform A/B testing through a dedicated use case
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
TQID: https://experienceleague.adobe.com/rYG71DezWYLaFpxjPKrnCEQJgyDVjFfopNsr6aWtQ1w
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer (Campaign)
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages (Campaign)
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing (Campaign)
  - id: e739ee2b-6228-412e-878f-45de0791417d
    internal-label: Use cases (Campaign)
---
# AB testing: A/B Testing this use case {#ab-testing-use-case}

In this use case, we are going to compare two email delivery contents via a targeting workflow. The message and the text are identical in both deliveries: only the layout changes.

The targeted population is divided into three: two test groups and the remaining population. A different version of the delivery is sent to each test group.

After the delivery, a 5-day wait period is configured before collecting the results of the best open rates. The content of the delivery with the highest score is then recovered by a script and sent to the population that was not used as a test group.

Please note that the criteria that will decide which delivery is the best may be altered to meet your needs. It can be the open rate, the click-through rate, the subscription rate, reactivity, etc.

Moreover, the test detailed in this use case related to two deliveries only, but you can test as many versions as necessary. Simply add activities to the workflow.

The main steps to perform this use case are:

* [Step 1: Create a targeting workflow](a-b-testing-uc-targeting-workflow.md)
* [Step 2: Configure population samples](a-b-testing-uc-population-samples.md)
* [Step 3: Create two delivery templates](a-b-testing-uc-delivery-templates.md)
* [Step 4: Configure the deliveries in the workflow](a-b-testing-uc-configuring-deliveries.md)
* [Step 5: Create the script](a-b-testing-uc-script.md)
* [Step 6: Define the final delivery](a-b-testing-uc-final-delivery.md)
* [Step 7: Start the workflow](a-b-testing-uc-start-workflow.md)
* [Step 8: Analyze the result](a-b-testing-uc-analyzing.md)

**Related topics:**

* [Get started with A/B testing](get-started-a-b-testing.md)
* [Configure A/B testing](configuring-a-b-testing.md)
