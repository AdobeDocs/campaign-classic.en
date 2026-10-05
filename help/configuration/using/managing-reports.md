---
product: campaign
title: Manage reports
description: Manage reports
feature: Reporting, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
TQID: 'https://experienceleague.adobe.com/LA4v5oODC9n5K2Ttox9SF7lwcGQOU7IDEvL1P4Sls-4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
---
# Manage reports{#managing-reports}

 

Reports based on a schema that is specific to the default Adobe Campaign recipients (nm:recipient or schema linked) must be re-developed in order to take into account the data from the custom table and its tables linked via the target mapping (see the [Target mapping](../../configuration/using/target-mapping.md) section).

To create new reports, refer to [this section](../../reporting/using/about-reports-creation-in-campaign.md).

In some cases, you must also put new cubes that are specific to these tables into place. Cubes are detailed in [this section](../../reporting/using/ac-cubes.md).

The following reports are concerned:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): real-time proposition tracking.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): opens broken down according to user software.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analysis of sharing activities, opens and subscriptions per time period.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): tracking indicators for a delivery on a mobile application.
* **[!UICONTROL Offer analysis]** (offerAnalysis): offer analysis per date and channel.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): reactivity rate for the latest deliveries.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): breakdown of active subscriptions per mobile application.
