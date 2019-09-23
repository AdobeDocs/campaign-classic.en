---
title: Monitoring marketing campaigns
seo-title: Monitoring marketing campaigns
description: Monitoring marketing campaigns
seo-description: 
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
---

## Tracking {#tracking}

### Tracking a campaign {#tracking-a-campaign}

For each campaign, the **[!UICONTROL Tracking]** tab lets you view all jobs and their statuses. The following information is accessible via this sub-tab:

* The activity journal shows the jobs carried out on the campaign in general: workflow creation or start, approval, extraction, etc.

  ![](assets/s_ncs_user_op_edit_exe_tab_a.png)

* The **[!UICONTROL Deliveries]** sub-tab contains all the deliveries of the campaign which can be edited from this view. To do so, select the delivery and click the **[!UICONTROL Detail]** icon.

  ![](assets/s_ncs_user_op_edit_exe_tab_b.png)

* The **[!UICONTROL Tasks]** sub-tab groups all tasks linked to the campaign. This view lets you edit them or delete them. Tasks are available with the MRM application. They are detailed in [Creating and managing tasks](../../campaign/using/creating-and-managing-tasks.md).

  ![](assets/s_ncs_user_op_edit_exe_tab_e.png)

* The workflows created to generate messages for service providers are displayed in the **[!UICONTROL Jobs on service providers]** sub-tab. Click the **[!UICONTROL Detail]** icon to display the selected workflow. 

  ![](assets/s_ncs_user_op_edit_exe_tab_d.png)

### Delivery tracking {#delivery-tracking}

The list of deliveries is available via the **[!UICONTROL Deliveries]** link of the Campaign node.

![](assets/s_ncs_user_op_del_state_from_homepage.png)

For each delivery, this list lets you access the key indicators: status, number of recipients targeted, linked campaigns, etc.

To check the status of a delivery, edit it and view its dashboard and tabs.

>[!NOTE]
>
>Information concerning delivery details is available in the [Sending Messages](../../delivery/using/about-message-tracking.md) section.

### Execution tracking {#execution-tracking}

You can look up the status of deliveries by clicking the **[!UICONTROL Deliveries]**, which is accessible via the Adobe Campaign home page. See [Delivery tracking](../../campaign/using/marketing-campaign-monitoring.md#delivery-tracking).

Information concerning the processes executed in a campaign are collected in the **[!UICONTROL Edit > Audit]** tab of the campaign. There, you can view the list of deliveries in the campaign. See [Tracking a campaign](../../campaign/using/marketing-campaign-monitoring.md#tracking-a-campaign).

### List of campaign process workflows {#list-of-campaign-process-workflows}

By default, the following workflows are available in the **Campaign process** folder but are created when the **Campaign** or **MRM** modules are installed:

* **Stocks: orders and warnings** (internal name:**stockMgt**): this workflow launches stock calculation on the order lines and manages warning thresholds.

  It is installed by default with the **Campaign** module.

* **Processes on service providers** (internal name: **supplierMgt**): this workflow launches service provider processes (email to the router and post-processing) once deliveries are approved.

  It is installed by default with the **Campaign** module.

* **Processes on campaigns** (internal name: **operationMgt**): this workflow manages processes on marketing campaigns (targeting, file extraction, etc.); It also creates the workflows related to recurring and periodic campaigns.

  It is installed by default with the **Campaign** module.

* **Processes on deliveries within campaigns** (internal name: **deliveryMgt**): this workflow sends approval notifications and reminders.

  It is installed by default with the **Campaign** module.

* **Task notification** (internal name: **taskMgt**: this workflow lets you send notification messages regarding tasks in marketing campaigns.

  It is installed by default with the **MRM** module.

* **Marketing resource notification** (internal name: **assetMgt**): this workflow manages notifications linked to approving and publishing marketing resources.

  It is installed by default with the **MRM** module.

* **Processes on distributed marketing** (internal name: **centralLocalMgt**): this workflow executes processes linked to using the distributed marketing module. It launches local campaign creation and manages notifications linked to orders and campaign package availability.

  It is installed by default with the **Central/local marketing campaign management** module.

* **Cost calculation** (internal name: **budgetMgt**): this workflow launches the calculation of expenditures and costs on budgets, plans, programs, campaigns, deliveries and tasks.

  It is installed by default with the **Campaign** module.

>[!CAUTION]
>
>These workflows MUST be started in order for the campaign processes to be executed at a campaign level.
