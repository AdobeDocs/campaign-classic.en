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

The targeted population is divided into three: two test groups and the remaining population. A different version of the delivery is sent to each test group. After the delivery, a 5-day wait period is configured before collecting the results of the best open rates. The content of the delivery with the highest score is then recovered by a script and sent to the population that wasn't used as a test group.

Please note that the criteria that will decide which delivery is the best may be altered to meet your needs. It can be the open rate, the click-through rate, the subscription rate, reactivity, etc.

Moreover, the test detailed in this use case concerns only two deliveries, but you can test as many versions as necessary. Simply add activities to the workflow.

To create the A/B test, apply the following steps:

* [Step 1: Creating a targeting workflow](#step-1--creating-a-targeting-workflow)
* [Step 2: Configuring population samples](#step-2--configuring-population-samples)
* [Step 3: Creating two delivery templates](#step-3--creating-two-delivery-templates)
* [Step 4: Configuring the deliveries in the workflow](#step-4--configuring-the-deliveries-in-the-workflow)
* [Step 5: Creating the script](#step-5--creating-the-script)
* [Step 7: Starting the workflow](#step-7--starting-the-workflow)
* [Step 8: Analyzing the result](#step-8--analyzing-the-result).

