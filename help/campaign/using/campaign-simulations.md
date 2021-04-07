---
solution: Campaign Classic
product: campaign
title: Campaign simulations
description: Campaign simulations
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
---
# Campaign simulations{#campaign-simulations}

## About simulations {#about-simulations}

Campaign Optimization lets you test the efficiency of a campaign plan using simulations. This lets you measure the potential success of a campaign: generated revenue, target volume based on the typology rules applied, etc.

Simulation lets you monitor and compare the impact of deliveries.

>[!NOTE]
>
>Deliveries prepared in Test mode have no impact on each other, for example when assessing a campaign in distributed marketing, or as long as the deliveries aren't scheduled in the provisional calendar.  
>This means that pressure and capacity rules are only applied to deliveries in **[!UICONTROL Target estimation and message personalization]** mode. Deliveries in **[!UICONTROL Estimation and approval of the provisional target]** and in **[!UICONTROL Target evaluation]** mode are not taken into account.  
>The delivery mode is chosen in the **[!UICONTROL Typology]** sub-tab of the delivery properties.

![](assets/simu_campaign_select_delivery_mode.png)

## Setting up a simulation {#setting-up-a-simulation}

### Creating a simulation {#creating-a-simulation}

To create a simulation, apply the following steps:

1. Open the **[!UICONTROL Campaigns]** tab, click the **[!UICONTROL More]** link within the **[!UICONTROL Create]** section and select the **[!UICONTROL Simulation]** option.

   ![](assets/simu_campaign_opti_01.png)

1. Enter the template and the name of the simulation. Click **[!UICONTROL Save]** to create the simulation.

   ![](assets/simu_campaign_opti_02.png)

1. Click the **[!UICONTROL Edit]** tab to configure it.

   ![](assets/simu_campaign_opti_edit.png)

1. In the **[!UICONTROL Scope]** tab, specify the deliveries you want to consider for this simulation. To do this, click the **[!UICONTROL Add]** button and specify the delivery selection mode to take into account.

   ![](assets/simu_campaign_opti_edit_scope.png)

   You can either select each delivery one by one or sort them by campaign, program or plan.

   >[!NOTE]
   >
   >If you select deliveries via a plan, program or campaign, Adobe Campaign can automatically refresh the list of deliveries to take into account whenever a simulation is started. To do this, check the **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** option.
   >  
   >If you don't do this, any deliveries that are not available in the plan, program, or campaign when the simulation is created will not be taken into account: deliveries added later will be ignored.

    ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Select the elements to include in the simulation scope. If necessary, select multiple elements using the SHIFT and CTRL keys.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Click **[!UICONTROL Finish]** to approve the selection.

   You can manually combine selected deliveries and deliveries belonging to plans, programs or campaigns.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   If necessary, you can use a dynamic condition via the **[!UICONTROL Edit the dynamic condition...]** link.

   Click **[!UICONTROL Save]** to approve this configuration.

   >[!NOTE]
   >
   >Only deliveries whose target has been calculated are taken into account when calculating simulations (statuses: **Target ready** or **Ready to deliver**).

1. In the **[!UICONTROL Calculations]** tab, select an analysis dimension such as the recipient schema for example.

   ![](assets/simu_campaign_opti_dimension.png)

1. You can then add expressions.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Execution settings {#execution-settings}

The **[!UICONTROL General]** tab of the simulation lets you enter execution settings:

* The **[!UICONTROL Schedule execution for down-time]** option defers the simulation launch to a less busy time period, based on the chosen level of priority. Simulations use significant database resources, that's why non-urgent simulations should be scheduled to run at night, for example.
* The **[!UICONTROL Priority]** is the level applied to the simulation to delay its triggering.
* **[!UICONTROL Save SQL queries in the log]**. SQL logs let you diagnose a simulation if it ends with errors. They can also help you find out why a simulation is too slow. These messages will be visible after the simulation in the **[!UICONTROL SQL logs]** sub-tab of the **[!UICONTROL Audit]** tab.

## Executing a simulation {#executing-a-simulation}

### Starting a simulation {#starting-a-simulation}

Once the simulation scope is defined, you can execute it.

To do this, open the simulation dashboard and click **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

Once execution is complete, open the simulation and click the **[!UICONTROL Results]** tab to view the targets calculated for each delivery.

![](assets/simu_campaign_opti_results.png)

1. The **[!UICONTROL Deliveries]** sub-tab lists all deliveries taken into account by the simulation. It shows two counts:

    * The **[!UICONTROL Initial count]** is the target as it was calculated during its estimation in the delivery. 
    * The **[!UICONTROL Final count]** is the number of recipients counted after simulation.

      The difference between initial and final counts reflects the application of the various rules or filters configured prior to the simulation.

      To learn more about this calculation, edit the **[!UICONTROL Exclusions]** sub-tab.

1. The **[!UICONTROL Exclusions]** sub-tab lets you view the exclusion break-down.

   ![](assets/simu_campaign_opti_14.png)

1. The **[!UICONTROL Alerts]** sub-tab groups all alert messages generated during the simulation. Alert messages can be sent in case of capacity overload (if the number of recipients targeted exceeds the set capacity, for instance).
1. The **[!UICONTROL Exploration of the exclusions]** sub-tab lets you create a result analysis table. The user needs to indicate variables in the abscissa/ordinates axes.

   For an example of analysis table creation, refer to the end of [Exploring results](#exploring-results).

### Viewing results {#viewing-results}

#### Audit {#audit}

The **[!UICONTROL Audit]** tab lets you monitor simulation execution. The **[!UICONTROL SQL Logs]** sub-tab is useful for expert users. It lists execution logs in SQL format. These logs are only displayed if the **[!UICONTROL Save SQL queries in the log]** option has been selected in the **[!UICONTROL General]** tab before simulation execution.

![](assets/simu_campaign_opti_11.png)

#### Exploring results {#exploring-results}

The **[!UICONTROL Exploration of the exclusions]** sub-tab lets you analyze the data resulting from a simulation.

Descriptive analysis is detailed in [this section](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Results of a simulation {#results-of-a-simulation}

The indicators in the **[!UICONTROL Log]** and **[!UICONTROL Results]** tabs provide a first overview of simulation results. For a more detailed view of results, open the **[!UICONTROL Reports]** tab.

### Reports {#reports}

To analyze the result of a simulation, edit its reports: they show exclusions and causes.

The following reports are provided by default:

* **[!UICONTROL Detail of simulation exclusions]** : this report provides a detailed chart of exclusion causes for all concerned deliveries.
* **[!UICONTROL Simulation summary]** : this report shows the populations excluded from the simulation throughout the various deliveries. 
* **[!UICONTROL Summary of exclusions linked to the simulation]** : this report shows a chart of exclusions caused by the simulation along with the applied typology rule and a chart showing the exclusion ratio per rule.

>[!NOTE]
>
>You can create new reports and add them to the ones offered. For more on this, refer to [this section](../../reporting/using/about-adobe-campaign-reporting-tools.md).

To access reports, click the **[!UICONTROL Reports]** link of the targeted simulation via its dashboard.

![](assets/campaign_opt_reporting_edit_from_board.png)

You can also edit reports using the **[!UICONTROL Reports]** link accessible from the simulation dashboard.

### Comparing simulations {#comparing-simulations-}

Each time a simulation is executed, the result replaces any previous results: you cannot display and compare results from one execution to another.

To compare results, you need to use reports. Indeed, Adobe Campaign lets you save a report history to view it again later. This history is saved throughout the simulations' life-cycle.

**Example:**

1. Create a simulation on a delivery which typology **A** is applied to.
1. In the **[!UICONTROL Reports]** tab, edit one of the available reports, such as **[!UICONTROL Detail of simulation exclusions]** for example.
1. In the upper right-hand section of the report, click the icon to create a new history.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Close the simulation and change the configuration of typology **A**.
1. Execute the simulation again and compare the result with the one displayed in the report for which a history was created.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   You can save as many report histories as necessary.

### Reporting axes {#reporting-axes}

The **[!UICONTROL Calculations]** tab lets you define reporting axes on the target. Theses axes will be used during result analysis (refer to [Exploring results](#exploring-results)).

>[!NOTE]
>
>We recommend defining calculation axes in the simulation templates rather than individually for each simulation.  
>Simulation templates are saved in the **[!UICONTROL Resources > Templates > Simulation templates]** node of the Adobe Campaign tree.

**Example:**

In the example below, we want to create an additional reporting axis based on the recipients' status ("Customer", "Prospect" or none).

1. To define a reporting axis, select the table which contains the information to be processed in the **[!UICONTROL Analysis dimension]** field. This information is mandatory.
1. Here, we want to select the Segment field of the recipient table.

   ![](assets/simu_campaign_opti_09.png)

1. The following options are available:

    * **[!UICONTROL Generate target overlap statistics]** lets you recover all overlap statistics in the simulation report. Overlaps are recipients targeted in at least two deliveries within one simulation.

      >[!IMPORTANT]
      >
      >Selecting this option considerably increases simulation execution time.

    * **[!UICONTROL Keep the simulation work table]** lets you keep simulation traces.

      >[!IMPORTANT]
      >
      >The automatic saving of these tables requires a significant storage capacity: make sure the database is big enough.

When the simulation results are displayed, the information on the selected expression will be displayed in the **[!UICONTROL Overlaps]** sub-tab.

Delivery target overlaps indicate the targeted recipients in at least two deliveries of a simulation.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>This sub-tab is only displayed if the **[!UICONTROL Generate target recovery statistics]** option has been enabled.

The information on reporting axes can be processed in exclusion analysis reports created in the **[!UICONTROL Exploring exclusions]** sub-tab. For more on this, refer to [Exploring results](#exploring-results).
