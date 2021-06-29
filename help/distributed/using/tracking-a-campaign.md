---
product: campaign
title: Tracking a campaign
description: Tracking a campaign
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
---
# Tracking a campaign{#tracking-a-campaign}

Central entity operators can track campaign orders in the list of campaign packages.

This lets them:

* [Filter packages](#filter-packages),
* [Edit packages](#edit-packages),
* [Cancel a package](#cancel-a-package),
* [Reinitializing a package](#reinitializing-a-package).

## Filter packages {#filter-packages}

From the **[!UICONTROL Campaigns]** tab, you can display the list of **[!UICONTROL Campaign packages]** which regroups all existing Distributed Marketing campaigns. You can filter this list so that it displays only campaigns that are either published, late, pending approval, etc. To do this, click the links in the upper section of this view, or use the **[!UICONTROL Filter list]** link and select the campaign package status to display.

![](assets/mkg_dist_catalog_filter.png)

## Edit packages {#edit-packages}

The **[!UICONTROL Campaign packages]** page lets you view the summary of each package.

This summary shows the following information: label, type of campaign, as well as the name of the campaign from which it was created, and the folder.

Click the package name to edit it. You can also view orders by their local entities and by their status.

This information is also offered in the **[!UICONTROL Campaign orders]** view which lists all orders.

![](assets/mkg_dist_catalog_op_command_details.png)

The central operator can edit the order. There are two ways of doing this:

1. The operator can click the order name to edit it: this displays the order details.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   The **[!UICONTROL Edit > General]** tab lets you view information entered by the local entity when it ordered the campaign.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. The operator can click the campaign package label to edit it and change certain settings.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Cancel a package {#cancel-a-package}

The central entity can cancel a campaign package at any time.

Click **[!UICONTROL Cancel]** in the campaign package **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

The **[!UICONTROL Comment]** field lets you justify the cancellation.

For **local campaigns**, canceling a package removes it from the list of available marketing campaigns.

For **collaborative campaigns**, canceling a package triggers numerous actions:

1. Any orders related to this package are canceled,

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. The reference campaign is canceled and all active processes (workflows, deliveries) are stopped,

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. A notification is sent to all local entities concerned.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

Canceled packages can still be accessed and reinitialized by the central entity (see below) if necessary. They will only be offered to local entities again once they have been approved and started. The package reinitialization process is shown below.

## Reinitializing a package {#reinitializing-a-package}

Campaign packages which have already been published can be reinitialized, modified and made available to local entities.

1. Select the package concerned.
1. Click the **[!UICONTROL Reinitialize the package to reuse it]** link and click **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Click the **[!UICONTROL Save]** button to approve package re-initialization.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. The package status changes to **[!UICONTROL Being edited]**. Modify, approve and publish it again to restore it to the list of campaign package.

>[!NOTE]
>
>You can also reinitialize canceled campaign packages.
