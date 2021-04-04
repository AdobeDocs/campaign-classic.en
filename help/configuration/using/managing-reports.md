---
solution: Campaign Classic
product: campaign
title: Managing reports
description: Managing reports
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
---
# Managing reports{#managing-reports}

Reports based on a schema that is specific to the default Adobe Campaign recipients (nm:recipient or schema linked) must be re-developed in order to take into account the data from the custom table and its tables linked via the target mapping (see the [Target mapping](../../configuration/using/target-mapping.md) section).

To create new reports, refer to [this section](../../reporting/using/about-reports-creation-in-campaign.md).

In some cases, you must also put new cubes that are specific to these tables into place. Cubes are detailed in [this section](../../reporting/using/about-cubes.md).

The following reports are concerned:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): real-time proposition tracking.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): opens broken down according to user software.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analysis of sharing activities, opens and subscriptions per time period.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): tracking indicators for a delivery on a mobile application.
* **[!UICONTROL Offer analysis]** (offerAnalysis): offer analysis per date and channel.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): reactivity rate for the latest deliveries.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): breakdown of active subscriptions per mobile application.
