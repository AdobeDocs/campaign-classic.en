---
title: Managing reports
seo-title: Managing reports
description: Managing reports
seo-description: 
page-status-flag: never-activated
uuid: 3b8e6f11-4cbd-450e-871b-50fd0ead96db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 21777423-0c8a-4bb1-b210-972f660648bd
index: y
internal: n
snippet: y
---

# Managing reports{#managing-reports}

Reports based on a schema that is specific to the default Adobe Campaign recipients (nm:recipient or schema linked) must be re-developed in order to take into account the data from the custom table and its tables linked via the target mapping (see the [Target mapping](https://helpx.adobe.com/campaign/standard/configuration/using/target-mapping.html) section).

To create new reports, refer to [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-reports-creation-in-campaign.html).

In some cases, you must also put new cubes that are specific to these tables into place. Cubes are detailed in [this section](https://helpx.adobe.com/campaign/classic/reporting/using/about-cubes.html).

The following reports are concerned:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): real-time proposition tracking.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): opens broken down according to user software.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analysis of sharing activities, opens and subscriptions per time period.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): tracking indicators for a delivery on a mobile application.
* **[!UICONTROL Offer analysis]** (offerAnalysis): offer analysis per date and channel.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): reactivity rate for the latest deliveries.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): breakdown of active subscriptions per mobile application.

