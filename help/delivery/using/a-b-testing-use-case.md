---
solution: Campaign Classic
product: campaign
title: About this use case
description: Learn how to perform A/B testing through a dedicated use case.
audience: delivery
content-type: reference
topic-tags: a-b-testing
---

# About this use case {#about-use-case}

In this use case, we are going to compare two email delivery contents via a targeting workflow. The message and the text are identical in both deliveries: only the layout changes.

The targeted population is divided into three: two test groups and the remaining population. A different version of the delivery is sent to each test group.

After the delivery, a 5-day wait period is configured before collecting the results of the best open rates. The content of the delivery with the highest score is then recovered by a script and sent to the population that was not used as a test group.

Please note that the criteria that will decide which delivery is the best may be altered to meet your needs. It can be the open rate, the click-through rate, the subscription rate, reactivity, etc.

Moreover, the test detailed in this use case related to two deliveries only, but you can test as many versions as necessary. Simply add activities to the workflow.

The main steps to perform this use case are:

* [Step 1: Create a targeting workflow](#step-1--creating-a-targeting-workflow)
* [Step 2: Configure population samples](#step-2--configuring-population-samples)
* [Step 3: Create two delivery templates](#step-3--creating-two-delivery-templates)
* [Step 4: Configure the deliveries in the workflow](#step-4--configuring-the-deliveries-in-the-workflow)
* [Step 5: Create the script](#step-5--creating-the-script)
* [Step 7: Start the workflow](#step-7--starting-the-workflow)
* [Step 8: Analyze the result](#step-8--analyzing-the-result).

**Related topics:**

* [Get started with A/B testing](../../delivery/using/get-started-a-b-testing.md)
* [Configure A/B testing](../../delivery/using/configuring-a-b-testing.md)
