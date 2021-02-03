---
solution: Campaign Classic
product: campaign
title: Get started with A/B testing
description: Learn more about A/B testing in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
---

# Get started with A/B testing {#get-started-a-b-testing}

A/B testing allows you to compare multiple version of a delivery against each other, in order to identify which one will have the biggest impact on the targeted population.

To do this, you need to define multiple variants of a delivery. Each variant is then sent to population samples in order to determine which one performs better depending on the criteria of your choice (opens, spam complaints, clicks on a specific link, ...). 

With Campaign Classic, A/B testing is implemented through workflows, where you specify the population to target as well as the groups that will receive each variant. Workflows also allow you to automate your processes by automatically identifying the delivery variant that performed better, then sending it to the remaining population.

In the example below, the delivery target has been splitted into two groups, each representing 50% of the targeted population. Each group receives two versions of the delivery with two different promotional offers. After the delivery is sent, it is concluded that variant A performed better, based on the number of clicks on the promotional offers.

![](assets/a-b-testing-schema.png)


Related topics:

* [Configuring a/b testing](../../delivery/using/configuring-a-b-testing.md)
* [Use case](../../delivery/using/a-b-testing-use-case.md)