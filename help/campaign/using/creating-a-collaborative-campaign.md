---
solution: Campaign Classic
product: campaign
title: Creating a collaborative campaign
description: Creating a collaborative campaign
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
---
# Creating a collaborative campaign{#creating-a-collaborative-campaign-intro}

The central entity creates collaborative campaigns from **Distributed Marketing** campaign templates. Refer to [this page](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Creating a collaborative campaign {#creating-a-collaborative-campaign}

To configure a collaborative campaign, click the **[!UICONTROL Campaign management > Campaigns]** node, then the **[!UICONTROL New]** icon.

>[!NOTE]
>
>Apart from **[!UICONTROL collaborative campaigns (by campaign)]**, these campaigns can be configured and executed via a web interface.

The configuration process for a collaborative campaign database is similar to that of a local campaign template. The specifications of the different types of collaborative campaigns are detailed below.

### By form {#by-form}

To create a collaborative campaign (by form), the **[!UICONTROL Collaborative campaign (by form)]** template must be selected.

![](assets/mkg_dist_mutual_op_form2.png)

In the **[!UICONTROL Edit]** tab, click the **[!UICONTROL Advanced campaign settings...]** link to access the **Distributed Marketing** tab.

Select the **By form** web interface. This type of interface lets you create personalization fields that will be used by local entities when ordering a campaign. Refer to [Creating a local campaign (by form)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Save your campaign. You can now use it from the **Campaign packages** view in the **Campaign** tab, by clicking the **[!UICONTROL Create]** button.

The **[!UICONTROL Campaign Package]** view allows you to use local campaign templates (out-of-the-box or duplicated), as well as reference campaigns for collaborative campaigns, with the aim of creating campaigns for your different organizational entities.

![](assets/mkg_dist_mutual_op_form1b.png)

### By campaign {#by-campaign}

To create a collaborative campaign (by campaign), the **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** template must be selected.

![](assets/mkg_dist_mutual_op_by_op2.png)

When ordering the campaign, the local entity can complete the criteria predefined by the central entity, and evaluate the campaign before ordering it.

Once an order for a **Collaborative campaign (by campaign)** is approved by the central entity, a child campaign is created for the local entity. Once available to them, the local entity can then modify:

* the campaign workflow,
* typology rules,
* and personalization fields.

The local entity executes the child campaign. The central entity executes the parent campaign.

The central entity can view all child campaigns linked with a **Collaborative campaign (by campaign)** from this dashboard (via the **[!UICONTROL List of associated campaigns]** link).

![](assets/mkg_dist_mutual_op_by_op.png)

### By target approval {#by-target-approval}

To create a collaborative campaign (by target approval), the **[!UICONTROL Collaborative campaign (by target approval)]** template must be selected.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>In this mode, the central entity doesn't need to specify the local entities.

The campaign workflow must integrate **Local approval** type activity. The activity parameters are as follows:

* **[!UICONTROL Action to perform]** : Target approval notification.
* **[!UICONTROL Distribution context]** : Explicit.
* **[!UICONTROL Data distribution]** : Local entity distribution.

**Local entity distribution** type data distribution must be created. The data distribution template lets you limit the number of records from a list of grouping values. In **[!UICONTROL Resources > Campaign management > Data distribution]**, click the **[!UICONTROL New]** icon to create a new **[!UICONTROL Data distribution]**. For more information on data distribution, refer to the [Workflows](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) guide.

![](assets/mkg_dist_data_distribution.png)

Select the **Targeting dimension** and the **[!UICONTROL Distribution field]**. For the **[!UICONTROL Assignment type]**, select **Local entity**.

In the **[!UICONTROL Distribution]** tab, add a field for each local entity and specify the value.

![](assets/mkg_dist_data_distribution2.png)

You can add a second **Target approval** after the **Delivery** type activity to configure a report on it.

In the campaign creation notification message, the local entity receives a contact list that has been predefined by the central entity parameters.

![](assets/mkg_dist_mutual_op_by_valid1.png)

The local entity can delete certain contacts based on the campaign content. 

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Simple {#simple}

To create a simple collaborative campaign, the **[!UICONTROL Collaborative campaign (simple)]** template must be selected.

## Creating a collaborative campaign package {#creating-a-collaborative-campaign-package}

To make a campaign available to local entities, the central entity must create a campaign package.

Apply the following steps:

1. In the **[!UICONTROL Navigation]** section on the **Campaigns** page, click the **[!UICONTROL Campaign packages]** link.
1. Click the **[!UICONTROL Create]** button.
1. The section at the top of the window lets you select the **[!UICONTROL New collaborative package (mutualizedEmpty)]** template.
1. Select the reference campaign.
1. Specify the label, folder and execution schedule for the campaign package.

### Dates {#dates}

The start and end dates define the campaign's visibility period in the list of campaign packages.

For **collaborative campaigns**, the central entity must specify the registration and personalization deadline.

>[!NOTE]
>
>The **[!UICONTROL Personalization deadline]** allows the central entity to choose a deadline by which the local entities must have delivered the documents (spreadsheets, images) to be used to configure the campaign. This is not a mandatory option. Side-stepping this date will not affect campaign implementation.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Audience {#audience}

The central entity must specify the local entities involved per campaign as soon as the collaborative campaign is created. 

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** cannot be approved unless the relevant local entities have been specified.

### Approval modes {#approval-modes}

For **collaborative campaigns**, you can specify the order approval mode.

![](assets/mkg_dist_edit_kit1.png)

In manual mode, the local entity needs to subscribe for the campaign in order to participate.

In automatic mode, the local entity is pre-subscribed for the campaign. It may cancel campaign subscription or modify its parameters without needing approval from the central entity.

![](assets/mkg_dist_edit_kit2.png)

### Notifications {#notifications}

Configuration for notifications is identical to notifications for a local entity. Refer to [this section](../../campaign/using/creating-a-local-campaign.md#notifications).

## Ordering a campaign {#ordering-a-campaign}

When a collaborative campaign is added to the list of campaign packages, the local entities belonging to the audience defined by the central entity are notified (the **collaborative campaigns (by target approval)** do not have a predefined audience). The message sent contains a link that lets you register for the campaign, as shown below:

![](assets/mkg_dist_mutual_op_notification.png)

This message also enables local entities to view the description entered by the central operator that created the package, as well as documents linked to the campaign. These do not belong to the campaign itself, although they provide additional information on it.

Once local operators have logged on via a web interface, they can enter personalized information to the collaborative campaign they wish to order:

![](assets/mkg_dist_mutual_op_command.png)

After a local entity has completed their registration, central entities are notified by email to approve their order.

![](assets/mkg_dist_mutual_op_valid_command.png)

For more on this, refer to the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## Approving an order {#approving-an-order}

The process for approving a collaborative campaign package order is the same as when doing so for a local campaign. Refer to [this section](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
