---
title: Simulation scope
seo-title: Simulation scope
description: Simulation scope
seo-description: 
page-status-flag: never-activated
uuid: d3145926-0a7e-455f-9b93-55be1b2a0518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: ef658468-e20b-45d9-a714-c152e55c1c79
index: y
internal: n
snippet: y
---

# Simulation scope{#simulation-scope}

## Definition of the scope {#definition-of-the-scope}

Open the **[!UICONTROL Scope]** tab to choose your settings.

The following items are mandatory:

* Environment or offer category.
* Offer space.
* Contact date. Offers that are not eligible on the contact date are not taken into account.
* Target population.

  If you don't configure a filter on your target, the entire recipient table will be taken into account.

* Number of propositions to be simulated per target.

  The recipient will receive this many propositions. For example, if you enter 5, each recipient will receive a maximum of 5 offer propositions. 

  ![](assets/offer_simulation_009.png)

To refine the offers to be taken into account for the simulation, you can add one or several themes (specified beforehand in the categories).

You can also choose to carry out the simulation on all the offers or only those that are online. Some filters allow you to alter your selection if you want to.

>[!NOTE]
>
>You must specify a contact date. This lets the interaction engine sort the offers in the selected environment or category. If no date is configured, the simulation will raise an error.

## Adding reporting axes {#adding-reporting-axes}

You can enhance the simulation analysis by adding reporting axes on the target or the offers themselves via the **[!UICONTROL Calculations]** tab.

To do this, click the **[!UICONTROL Add]** button and choose the appropriate fields. Axes will be used for calculating the simulation and are displayed in the analysis report. For more on this, refer to [Simulation tracking](https://helpx.adobe.com/campaign/standard/interaction/using/simulation-tracking.html).

![](assets/offer_simulation_011.png)

