---
title: Execution settings
seo-title: Execution settings
description: Execution settings
seo-description: 
page-status-flag: never-activated
uuid: 9eea7fe2-4033-48c3-9229-106e185f0fd9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
discoiquuid: 96ddc929-6a93-495f-ae32-768eecb3a670
index: y
internal: n
snippet: y
---

# Execution settings{#execution-settings}

When creating a simulation, you can specify execution settings if necessary. These settings let you execute the simulation during a time of low activity depending on its priority, or record SQL queries in the log. This stage is optional.

These settings can be changed later in the **General** tab of the simulation window.

![](assets/offer_simulation_008.png)

* **Schedule execution for a time of low activity**: lets you schedule the simulation based on the chosen priority (Low, Average or High) in order to optimize Adobe Campaign performances.
* **Priority**: this is the level applied to the simulation to schedule it. When the **Schedule execution for a time of low activity** option is checked, the campaign processing workflow selects a time of low activity to start the campaign.
* **Log SQL queries in the journal**: this functionality is for expert users only. It lets you add a tab to the log displaying SQL queries to detect possible malfunctions if the simulation finishes with errors.

