---
title: About profiles
seo-title: About profiles
description: About profiles
seo-description: 
page-status-flag: never-activated
uuid: 9ef75283-ac70-4f84-b527-a9c44912b62e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: a5b14846-ef26-433a-8bad-bcab653ea598
index: y
internal: n
snippet: y
---

# About profiles{#about-profiles}

## Profile types {#profile-types}

Adobe Campaign lets you manage profiles throughout their entire lifecycle: creation, import, targeting, action tracking, updates, etc.

Each profile matches a database entry. They contain all the information required for targeting, qualifying and tracking individuals.

Profiles can be identified based on storage space. This means that a profile can match: a recipient, a visitor, an operator, a subscriber, a prospect, etc.

## Recipient profiles {#recipient-profiles}

Delivery recipients are stored in the database as profiles containing the information linked to them: last name, first name, address, subscriptions, deliveries, etc. When you create campaigns, you can define the target of the deliveries to a selection of the profiles in the base according to simple or advanced criteria.

You can also create campaigns aimed at recipients whose profiles are stored not in the database, but in files. These are known as "external" deliveries. For more information about this type of delivery, refer to [this page](../../delivery/using/key-steps-when-creating-a-delivery.md#selecting-external-recipients).

The main methods for creating recipient profiles are as follows:

* direct input in the graphical interface screens,
* importing recipient lists,
* on-line collection via web forms.

>[!NOTE]
>
>To find out how files and web forms are imported, refer to [Generic imports and exports](../../platform/using/generic-imports-and-exports.md).

## Profiles and targets {#profiles-and-targets}

The **Profiles and targets** link lets you display recipients stored in Adobe Campaign database. You can create new recipient, edit an existing recipient and access its profile. For more on this, refer to [this page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

It also gives you access to:

* lists; see [Creating and managing lists](../../platform/using/creating-and-managing-lists.md),
* subscription services; refer to [this page](../../delivery/using/managing-subscriptions.md),
* web applications; refer to [this page](../../web/using/about-web-applications.md),
* imports and exports (jobs); refer to [Generic imports and exports](../../platform/using/generic-imports-and-exports.md),
* targeting workflows; refer to [this page](../../workflow/using/building-a-workflow.md#implementation-steps-).

The recipients page lets you perform frequent operations on profiles: edits, updates, adds, deletions, sorts.

For more advanced profile manipulations, you need to edit the Adobe Campaign tree. To do this, click the **Explorer** link on the Adobe Campaign home page.

By default, recipients are stored in the **Profiles and Targets > Recipients** node of the tree. You can create recipients from this view, as well as:

* sort and filter the profiles of the database; see [Filtering options](../../platform/using/filtering-options.md),
* move, copy or delete profiles from the database; see [Managing profiles](../../platform/using/managing-profiles.md),
* update profiles; see [Updating data](../../platform/using/updating-data.md),
* export recipients; see [Exporting and importing profiles](../../platform/using/exporting-and-importing-profiles.md),
* create recipient groups; see [Creating and managing lists](../../platform/using/creating-and-managing-lists.md).

To access advanced functionalities and configurations, you need to click the **Explorer** icon. 

![](assets/d_ncs_user_interface01.png)

The general layout of the Adobe Campaign explorer is presented in [Using Adobe Campaign explorer](../../platform/using/about-profiles.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>You can also display an advanced view of this list from the Adobe Campaign tree by clicking the **Profiles and targets > Recipients** link. The list display can be configured to suit your needs. You can add or delete columns, define column order, sort data, etc. List display configuration is described in [Using Adobe Campaign explorer](../../platform/using/about-profiles.md#using-adobe-campaign-explorer).  
>You can also define recipient views. For further information about this functionality, refer to [Folders and views](../../platform/using/about-profiles.md#folders-and-views).

## Active profiles {#active-profiles}

Active profiles are the profiles that are counted for billing purposes.

“**Profile**” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead.

Billing only concerns profiles that are **active**. A profile is considered active if the profile has been targeted or communicated with in the past 12 months via any channel.

>[!NOTE]
>
>Facebook and Twitter channels are not taken into account.

You can have an overview of the **Number of active profiles** from the **Administration > Campaign Management > Customer metrics** menu.

The actual count is performed by the **Number of active billing profiles** (**billingActiveContactCount**) [technical workflow](../../workflow/using/delivery.md), which runs every day and adds the new data to the existing report for the current period in the **Customer metrics** menu. Each period lasts for 12 months.

The profiles that were excluded during delivery preparation (typology rules, quarantines) are not taken into account. A profile that has been targeted by several deliveries will only be counted once.
