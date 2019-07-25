---
title: Defining a conditional content
seo-title: Defining a conditional content
description: Defining a conditional content
seo-description: 
page-status-flag: never-activated
uuid: ce2e28c5-c2ea-42ad-8676-c30c69c17003
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: reporting
discoiquuid: bc340c37-22f3-4b53-9312-eb404d72928d
index: y
internal: n
snippet: y
---

# Defining a conditional content{#defining-a-conditional-content}

You can condition the display of specific report items or pages.

To make specific items conditional, adapt their visibility settings. For more on this, refer to [Conditioning item display](../../reporting/using/defining-a-conditional-content.md#conditioning-item-display).

To make the display of one or more pages conditional, use a **Test** type activity. For more on this, refer to [Conditioning page display](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display).

## Conditioning item display {#conditioning-item-display}

To make the display of part of a report conditional, you need to define its visibility conditions: if these aren't met, the items will not be displayed.

Visibility conditions may depend on the operator status, on the items selected or entered in the report page.

Examples showing the conditional display of items on a page are provided in [this section](../../web/using/form-rendering.md#defining-fields-conditional-display).

In the following example, the display condition depends on the language:

![](assets/reporting_display_condition.png)

## Conditioning page display {#conditioning-page-display}

In the chart of a report, the **Test** activity lets you change the sequence of pages depending on one or more conditions.

This activity is based on the following operating principle:

1. Place a **Test** in a chart and edit it.
1. Click the **Add** button to create the various possible cases.

   ![](assets/reporting_test_sample.png)

   For each case, an output transition is added to the **Test** activity.

   ![](assets/reporting_test_transitions.png)

1. Select the **Enable default transition** to add a transition, in case one of the configured conditions isn't met.

   For more on this, refer to [this section](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

A **Test** activity can be placed at the start of the chart to condition the display depending on context or operator profile for instance.
