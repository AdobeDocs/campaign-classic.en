---
solution: Campaign Classic
product: campaign
title: Building a workflow
description: Learn how to build a workflow
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
---
# Building a workflow {#building-a-workflow}

This section details the key principles and best practices to build a workflow in Campaign.

* Create a workflow, see [Creating a new workflow](#creating-a-new-workflow)
* Design the workflow diagram, see [Adding and linking activities](#adding-and-linking-activities)
* Access parameters and properties of activities, see [Configuring activities](#configuring-activities)
* Design targeting workflows, see [Targeting workflows](#targeting-workflows)
* Use workflows to execute a campaign, see [Campaign workflows](#campaign-workflows)
* Access and create technical workflows, see [Technical workflows](#technical-workflows)
* Use templates to create workflows, see [Workflow templates](#workflow-templates)

## Creating a new workflow {#creating-a-new-workflow}

From the **[!UICONTROL Explorer]**, access a workflow folder. By default, you can use **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.

Click the **[!UICONTROL New]** button located above the list of workflows. 

![](assets/create_a_wf_icon.png)

Or, you can also use the **[!UICONTROL Create]** button in the workflow overview (**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]** link).

![](assets/create_a_wf.png)

Enter a label and click **[!UICONTROL Save]**.

>[!NOTE]
>
>When you modify the internal name of a workflow activity or the workflow itself, make sure that you save the workflow before closing it so that the new internal name is correctly taken into account.

## Adding and linking activities {#adding-and-linking-activities}

You must now define the various activities and link them together in the diagram. At this stage of the configuration, we can see the diagram label and the workflow status (Editing in progress). The lower section of the window is used for editing the diagram only. It contains a toolbar, a palette of activities (on the left) and the diagram itself (on the right).

![](assets/new-workflow-2.png)

>[!NOTE]
>
>If the palette is not shown, click the first button on the toolbar to display it.

Activities are grouped by category inside the different tabs of the palette. Available tabs and activities can vary depending on the workflow type (technical, targeting or campaign workflow).

* The first tab contains targeting and data manipulation activities. These activities are detailed in [Targeting activities](../../workflow/using/about-targeting-activities.md).
* The second tab contains the scheduling activities, which are mainly used for coordinating other activities. These activities are detailed in [Flow control activities](../../workflow/using/about-flow-control-activities.md).
* The third tab contains tools and actions that can be used in the workflow. These activities are detailed in [Action activities](../../workflow/using/about-action-activities.md).
* The fourth tab contains activities that depend on a given event, such as the receipt of an email or the arrival of a file on a server. These activities are detailed in [Event activities](../../workflow/using/about-event-activities.md).

To create the diagram

1. Add an activity by selecting it in the palette and by moving it to the diagram using a drag-and-drop operation.

   Add a **Start** activity and then a **Delivery** activity on the diagram.

   ![](assets/new-workflow-3.png)

1. Link the activities together by dragging the **Start** activity transition and dropping it on to the **Delivery** activity.

   ![](assets/new-workflow-4.png)

   You can automatically link an activity to the previous one by placing the new activity at the end of the transition.

1. Add the activities you need and link them together as shown in the diagram below.

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>You can copy and paste activities within a same workflow. However, we do not recommend to copy paste activities across different workflows. Some settings attached to activities like Deliveries and Scheduler could lead to conflicts and errors while executing the destination workflow. Instead, we recommended you to  **Duplicate** workflows. For more information, see [Duplicating workflows](#duplicating-workflows).

You can change the display and layout of the chart using the following elements:

* **Using the toolbar**

  The diagram editing toolbar gives you access to the layout and execution functions of the workflow.

  ![](assets/s_user_segmentation_wizard_10.png)

  This lets you adapt the layout of the editing tool: display of the palette and the overview, size and alignment of graphical objects.

  ![](assets/s_user_segmentation_toolbar.png)

  Icons related to tracking and launching an advanced targeting workflow are detailed in this [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **Object alignment**

  To align icons, select them and click the **[!UICONTROL Align vertically]** or **[!UICONTROL Align horizontally]** icon.

  Use the **CTRL** key to select several scattered activities or to deselect one or more activities. Click on the diagram background to deselect everything.

* **Image management**

  You can customize the background image of the diagram as well as those related to the various activities. Refer to [Managing activity images](../../workflow/using/managing-activity-images.md).

## Configuring activities {#configuring-activities}

Double-click an activity to configure it or right-click and select **[!UICONTROL Open...]**.

>[!NOTE]
>
>Campaign workflow activities are detailed in [this section](../../workflow/using/about-activities.md).

The first tab contains the basic configuration. The **[!UICONTROL Advanced]** tab contains the additional parameters, which are used particularly for defining behavior when an error is encountered, specifying the execution duration for an activity, and for entering an initialization script.

For a better understanding of the activities and to improve workflow legibility, you can enter comments in the activities: these will be displayed automatically when operators scroll over the activity.

![](assets/example1-comment.png)

## Targeting workflows {#targeting-workflows}

Targeting workflows enable you to build several delivery targets. You can create queries, define unions or exclusions based on specific criteria, add scheduling, thanks to workflow activities. The result of this targeting can be transferred automatically to a list which can serve as the target of delivery actions

In addition to these activities, Data Management options let you manipulate data and access advanced functions to satisfy complex targeting issues. For more on this, refer to [Data Management](../../workflow/using/targeting-data.md#data-management).

All these activities can be found in the first workflow tab.

>[!NOTE]
>
>Targeting activities are detailed in [this section](../../workflow/using/about-activities.md).

Targeting workflows can be created and edited via the **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** node of the Adobe Campaign tree or via the **[!UICONTROL Profiles and Targets > Targeting workflows]** menu of the home page.

![](assets/target_wf.png)

Targeting workflows within the framework of a campaign are stored with all campaign workflows.

### Key steps to create a targeting workflow {#implementation-steps-}

Steps to create a targeting workflow are detailed in these sections:

1. **Identify** data in the database -  See [Creating queries](../../workflow/using/targeting-data.md#creating-queries)
1. **Prepare** data to meet delivery needs - See [Enriching and modifying data](../../workflow/using/targeting-data.md#enriching-and-modifying-data)
1. **Use** data to perform updates or within a delivery - See [Updating the database](../../workflow/using/how-to-use-workflow-data.md#updating-the-database)

The results of all enrichments and all handlings carried out during targeting are stored and accessible in personalization fields, in particular for use when creating personalized messages. For more on this, refer to [Target data](../../workflow/using/data-life-cycle.md#target-data)

### Targeting and filtering dimensions {#targeting-and-filtering-dimensions}

During data segmentation operations, the targeting key is mapped to a filtering dimension. The targeting dimension lets you define the population targeted by the operation: recipients, contract beneficiaries, operator, subscribers, etc. The filtering dimension lets you select the population based on certain criteria: contract holders, newsletter subscribers, etc.

For example, to select clients who have had a life-insurance policy for over 5 years, select the following targeting dimension: **Clients** and the following filtering dimension: **Contract holder**. You can then define the filtering conditions within the query activity

During the targeting dimension selection stage, only compatible filtering dimensions are offered in the interface.

These two dimensions must be related. Thus, the content of the **[!UICONTROL Filtering dimension]** list depends on the targeting dimension specified in the first field.

For example, for recipients (**recipient**), the following filtering dimensions will be available:

![](assets/query_filter_target_dimensions_1.png)

While for **Web Applications**, the list will contain the following filtering dimensions:

![](assets/query_filter_target_dimensions_2.png)

## Campaign workflows {#campaign-workflows}

For each campaign, you can create workflows to be executed from the **[!UICONTROL Targeting and workflows]** tab. These workflows are specific to the campaign.

![](assets/wf-in-op-edit-delivery-tab.png)

This tab contains the same activities as for all workflows. [Learn more](#implementation-steps-)

In addition to targeting campaigns, campaign workflows enable you to create and configure deliveries entirely for all available channels. Once created in the workflow, these deliveries are available from the dashboard of the campaign. [Learn more](../../campaign/using/marketing-campaign-deliveries.md)

All campaign workflows are centralized under the **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** node.

![](assets/campaigns_wf.png)

Campaign workflows and implementation examples are detailed in [this page](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

## Technical workflows {#technical-workflows}

Technical workflows are provided out-of-the-box with Adobe Campaign. They are operations or jobs scheduled for periodic execution on the server. They let you carry out maintenance on the database, forward tracking information on deliveries and set up provisional processes on deliveries. Technical workflows are configured via the **[!UICONTROL Administration > Production > Technical workflows]** node.

![](assets/navtree.png)

Native templates are available for creating technical workflows. They can be configured to suit your needs.

The **[!UICONTROL Campaign process]** subfolder centralizes the workflows required for executing processes within the campaigns: task notification, stock management, cost calculation, etc.

>[!NOTE]
>
>The list of technical workflows installed with each module is available in a [dedicated section](../../workflow/using/about-technical-workflows.md).

You can create other technical workflows in the **[!UICONTROL Administration > Production > Technical workflows]** node of the tree structure. However, this process is reserved for expert users.

The activities offered are the same as for targeting workflows. [Learn more](#implementation-steps-)

## Workflow templates {#workflow-templates}

Workflow templates contain the overall configuration of properties and possibly a range of activities concatenated within a diagram. This configuration can be reused for creating new workflows containing a certain number of pre-configured elements

You can create new workflow templates based on existing templates or change a workflow into a template directly.

Workflow templates are stored in the **[!UICONTROL Resources > Templates > Workflow templates]** node of the Adobe Campaign tree.

![](assets/s_advuser_wf_template_tree.png)

In addition to the usual workflow properties, the template properties allow you to specify the execution file for workflows created based on this template.

![](assets/s_advuser_wf_template_properties.png)

## Duplicating workflows {#duplicating-workflows}

You can duplicate different types of workflows. Once duplicated, modifications of the workflow are not carried over to the copy of the workflow.

>[!CAUTION]
>
>Copy-paste is available in workflows but we recommend you to use **Duplicate**. Once an activity copied, its whole configuration is kept. For delivery activities (Email, SMS, Push Notification...), the delivery object attached to the activity is also copied which can lead to crash.

1. Right-click on a workflow.
1. Click **Duplicate**.

     ![](assets/duplicate-workflows.png)

1. In the workflow window, change the workflow label.
1. Click **Save**.

The duplicate feature is not directly available in the view of a campaign.

Yet, you can create a view to display all the workflows on your instance. In this view, you can duplicate workflows using **Duplicate to**.

**First, let's create a view:**

1. In **Explorer**, go to the folder you need to create your view in.
1. Right-click and go to **Add a new folder** > **Process**, select **Workflows**.

    ![](assets/add-new-folder-workflows.png)

The new folder **Workflows** is created.

1. Right-click and select **Properties**.
1. In **Restriction**, check **Folder is a view** and click **Save**.

    ![](assets/folder-is-a-view.png)

The folder is now populated with all the workflows of your instance.

**Duplicating a campaign workflow**

1. Select a campaign workflow in the workflow view.
1. Right-click **Duplicate to**.
    ![](assets/duplicate-to-right-click.png)
1. Change its label.
1. Click **Save**.

You can see your duplicated workflow in the workflow view.
