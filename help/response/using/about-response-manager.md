---
product: campaign
title: About response manager
description: About response manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
---
# Get started with Campaign Response Manager{#about-response-manager}

![](../../assets/common.svg)

Adobe Campaign offers a Response Management add-on that lets you measure the success and profitability of marketing campaigns or offer propositions across communication channels: email, mobile, direct mail, etc.

## Hypothesis {#hypothesis-concept}

Hypotheses can be configured over a given period from the contact date to deduce the behavior of those targeted after receiving a delivery. These hypotheses are based on a **transaction** table that saves purchases and details of these purchases.

Hypotheses are limited in time and can be applied to a control group to be compared to the target population. Hypothesis results are provided by **indicators** that are updated automatically once the calculation is complete. The ROI linked to the hypotheses will be taken into account in the campaign reports.

Also, the **reports** provided with Response Manager enable you to summarize the information linked to turnover increase, margin calculation, as well as the ROI of the delivery or the offer.

In addition, thanks to the purchase detail lines, you can specify your hypotheses to focus only on one particular product for example.

For example, following a delivery promoting an item, we wish to evaluate the revenue generated. We apply the hypothesis that any recipient who has purchased at least one item in the month following the triggering of the delivery has reacted to this action. Response management will determine, based on this hypothesis, which purchase request lines should be assigned to it. Then, based on this, it will be possible to determine the resulting revenue as the sum of these lines.

>[!CAUTION]
>
>Response Manager is a **[!UICONTROL Campaign]** option. Please check your license agreement.

You can also calculate all the reactions for the entire household of the recipient that received the delivery or offer.

Each hypothesis is linked to a single transaction table. One delivery or offer can be linked to multiple hypotheses.

## Implementation steps {#method}

Before you start using Response Manager, refer to [Configuration](configuration.md) and carry out the necessary configurations.

In order to launch a hypothesis on a delivery or an offer, you need to define its context in a template which will be used for each hypothesis you create.

To define and create measuring hypotheses, apply the following process:

1. Define a hypothesis model. [Learn more](hypothesis-templates.md#creating-a-hypothesis-model)
1. Create one or more hypotheses on an existing delivery. [Learn more](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   or

   Create one or more hypotheses on offers. [Learn more](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Check hypothesis results. [Learn more](hypothesis-tracking.md)
1. Re-launch hypotheses if necessary. [Learn more](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
