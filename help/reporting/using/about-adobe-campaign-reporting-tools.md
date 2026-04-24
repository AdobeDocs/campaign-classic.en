---
product: campaign
title: About Adobe Campaign reporting tools
description: Analyze the success of your campaigns in build-in or customized reports
feature: Reporting, Monitoring
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
TQID: https://experienceleague.adobe.com/4D-bCeMQakNjr7OXhiZ1u0Sfp5MZWwzZzHtykBfFzZ8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
---
# Get started with reporting {#about-adobe-campaign-reporting-tools}

 

In addition to [built-in reports](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign lets you generate reports in various contexts and to meet different needs. Principles of use and implementation modes are detailed in this document.

Adobe Campaign isn't a specialized reporting tool: reports created in Adobe Campaign mainly enable you to view aggregated data. Adobe Campaign reports, which are dedicated to analyzing and representing data, are not designed for database exports.

To export data from the Adobe Campaign database, you need to create a workflow and use a data export activity. For more on this, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html){target="_blank"}.

Adobe Campaign provides several reporting tools:

1. **Built-in reports**: Adobe Campaign offers a set of reports on deliveries, campaigns, platform activities, optional functionalities, etc. These reports are available via the various functionalities which they relate to. They can be adapted to suit your specific needs.

   For more on this, refer to [this section](../../reporting/using/about-campaign-built-in-reports.md).

1. **Descriptive data analysis**: Adobe Campaign provides a visual tool for producing statistics on the data in the database. You can create descriptive analysis reports using a dedicated assistant and adapt their content and layout depending on your needs.

   For more on this, refer to [this section](../../reporting/using/about-descriptive-analysis.md).

1. **Personalized reports**: Adobe Campaign enables you to create reports on the data in the database. Once these have been created, they are made accessible in the appropriate contexts.

   Depending on the complexity of the queries, calculations and volumes, the data analyzed in these reports can be collected via a query and pre-aggregated in a list ('data management' type workflow) or in a Cube (using Marketing Analytics). It will be displayed in the form of a pivot table or a group list.

   For more on this, refer to [this section](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Analysis reports**: Marketing Analytics enables intuitive data exploration.

   For more on this, refer to [this section](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>For easy display and manipulation, as well as efficient exporting, reports must not contain more than 1,000 lines.
