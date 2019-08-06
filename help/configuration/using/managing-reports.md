---
title: Managing reports
seo-title: Managing reports
description: Managing reports
seo-description: 
page-status-flag: never-activated
uuid: ce2a113c-6b84-46ff-89e6-f10eb82eae1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 0b8b3966-71c9-45d9-a723-704a14de0f6a
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

