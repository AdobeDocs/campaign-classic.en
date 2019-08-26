---
title: Analyzing needs
seo-title: Analyzing needs
description: Analyzing needs
seo-description: 
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
index: y
internal: n
snippet: y
---

# Analyzing needs{#analyzing-needs}

Using a reporting tool depends on the volume of data to manipulate, its complexity, and on the type of reporting to be set up.

To optimize the creation, use and durability of a report, you need to take a close look at the needs which you want to meet. This first analysis will enable you to identify the type of report to create and the best creation mode. To create the report, apply the following steps:

1. Identify the need

   The first step is to clearly identify the need: what you want to show in your report and what its goal is (monitoring, analysis, data export, etc.).

   Adobe Campaign offers a wide range of reporting capacities. It is important to analyze your need to identify the most suitable functionality.

   For instance, you can:

    * Explore the data in the database and define measurements (via [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-cubes.html)),
    * Add indicators to an existing report (refer to [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-reports-creation-in-campaign.html)),
    * View the data in the database (via [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-descriptive-analysis.html)),
    * Create a new delivery report (refer to [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-reports-creation-in-campaign.html)),
    * Export data from the Adobe Campaign database (via a workflow, refer to [this section](https://helpx.adobe.com/campaign/classic/workflow/using/about-workflows.html)),
    * Create a pivot table (refer to [this section](https://helpx.adobe.com/campaign/classic/reporting/using/creating-a-table.html#creating-a-breakdown-or-pivot-table)),
    * Explore aggregated data (via [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-cubes.html)),
    * Use a wizard to analyze data (via [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-descriptive-analysis.html)),
    * Analyze large volumes of data (refer to [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-reports-creation-in-campaign.html)), etc.

1. Identify the target population

   Then you need to find out who the report you want to create will target, know the kind of public who will view it and the report display mode (in a browser, in Adobe Campaign, for a specific object, for the entire platform, etc.).

   You can also create reports for:

    * All Adobe Campaign operators,
    * Operators with the rights to access a marketing campaign only,
    * A single operator for temporary use,
    * All operators in Web access, etc.

   These considerations also need to take into account the issues linked to access rights and security.

1. Define the content

   Then you need to find out what type of data you want to display: delivery indicators, reports on the database profiles, etc.

   You also need to know the nature of this data (simple, resulting from a calculation, significant, etc.), its location (in Adobe Campaign, in a third-party system), its update frequency to define the calculation periodicity (daily, weekly, on-the-fly), as well as its volume.

   The issues linked to data volumes and updates need to be looked into carefully to avoid report display problems, especially in terms of time. We therefore recommend creating aggregates to pre-calculate some data outside of the report. Tables that contain the tracking and delivery logs can include millions of records: this means the data needs to be aggregated via a workflow to be used in a report.

