---
title: Managing reports
seo-title: Managing reports
description: Managing reports
seo-description: 
page-status-flag: never-activated
uuid: d91096aa-63a2-4d00-9eb5-e59fccf59cb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: a7daac3a-befc-42cd-b915-9bf8f1715d56
index: y
internal: n
snippet: y
---

# Managing reports{#managing-reports}

Reports based on a schema that is specific to the default Adobe Campaign recipients (nm:recipient or schema linked) must be re-developed in order to take into account the data from the custom table and its tables linked via the target mapping (see the [Target mapping](../../configuration/using/target-mapping.md) section).

To create new reports, refer to [this section](../../reporting/using/about-reports-creation-in-campaign.md).

In some cases, you must also put new cubes that are specific to these tables into place. Cubes are detailed in [this section](../../reporting/using/about-cubes.md).

The following reports are concerned:

* **Recent proposition tracking** (recentPropositions): real-time proposition tracking.
* **Breakdown of opens** (opensByUserAgent): opens broken down according to user software.
* **Statistics of the sharing activities** (forwardActivities): analysis of sharing activities, opens and subscriptions per time period.
* **Tracking indicators** (mobileAppDeliveryFeedback): tracking indicators for a delivery on a mobile application.
* **Offer analysis** (offerAnalysis): offer analysis per date and channel.
* **Reactivity rate** (mobileAppDistribution): reactivity rate for the latest deliveries.
* **Breakdown of subscriptions** (mobileAppDistribution): breakdown of active subscriptions per mobile application.

