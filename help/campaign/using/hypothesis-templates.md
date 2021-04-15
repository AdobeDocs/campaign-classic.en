---
solution: Campaign Classic
product: campaign
title: Hypothesis templates
description: Hypothesis templates
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 428c7677-454b-4618-bae7-0be7df6dfcaa
---
# Hypothesis templates{#hypothesis-templates}

## Creating a hypothesis model {#creating-a-hypothesis-model}

Configuring the hypothesis template lets you define the context for measuring reactions, whether for a delivery or for an offer. This is where the various measuring tables are referenced, including those for defining relations between individuals, hypotheses and the transaction table.

To create a hypothesis template, apply the following steps:

1. In the Adobe Campaign explorer, click **[!UICONTROL Resources>Templates>Hypothesis templates]**.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Click **[!UICONTROL New]** or right-click in the list of templates and choose **[!UICONTROL New]** in the drop-down list.
1. Enter the hypothesis label.
1. Specify whether the template is destined for hypotheses on offers or deliveries via the **[!UICONTROL Hypothesis type]**.
1. For **[!UICONTROL Delivery]** type templates, specify whether measurements should be carried out with or without a control group (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. For **[!UICONTROL Delivery]** type templates, you can choose a specific channel or decide to apply the template to all available channels in Adobe Campaign using the **[!UICONTROL Channel]** drop-down list (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. Select the **[!UICONTROL Execution folder]** in which you wish to create and automatically execute the hypotheses that will be created from this template.
1. Choose the execution settings (for more on this, refer to [Hypothesis template execution settings](#hypothesis-template-execution-settings)).
1. Specify the hypothesis calculation period (for more on this, refer to [Hypothesis template execution settings](#hypothesis-template-execution-settings)).

   >[!CAUTION]
   >
   >This period is determined from the contact date.

1. In the **[!UICONTROL Transactions]** tab, specify the tables and fields required for the hypothesis calculation (for more on this, refer to [Transactions](#transactions)).
1. If your template is configured for **[!UICONTROL Offer]** type hypotheses, you can enable the **[!UICONTROL Update offer proposition status]** option: in this case, select the status of the offer proposition you want to change.
1. Specify the scope of the hypothesis application (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).
1. If necessary, use a script to complete filtering (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).

### Properties of a hypothesis template {#properties-of-a-hypothesis-template}

The template's **[!UICONTROL General]** tab lets you specify the general template options. The available fields are:

* **[!UICONTROL Hypothesis type]**: lets you determine whether the template should be destined for hypotheses on deliveries or offers.

  You can also choose to create a hypothesis that will apply to both deliveries and offers.

  >[!NOTE]
  >
  >If the template applies to offers, the **[!UICONTROL Update offer proposition status]** option is available in the **[!UICONTROL Transactions]** tab.

* **[!UICONTROL Measurement with control group]**: lets you state whether a control group has been defined for the delivery or the campaign and include it in measurement indicators. The control group, which doesn't receive deliveries, lets you measure the impact of the campaign after the delivery, by comparing it with the target population which did receive the delivery.

  >[!NOTE]
  >
  >If the template is configured to take a control group into account, but no group is defined in the delivery which the hypotheses concern, the results will be based on targeted recipients only.

  For more on defining and configuring a control group, refer to [Defining a control group](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

* **[!UICONTROL Channel]**: you can choose a specific channel or make the hypothesis template available to all channels in the Adobe Campaign console by selecting **[!UICONTROL All channels]** in the drop-down list. If you configure the template for a specific channel, this lets you automatically filter deliveries per channel when creating the hypothesis (refer to [Creating hypotheses](../../campaign/using/creating-hypotheses.md)). 

  ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**: lets you specify the execution folder for the hypothesis.
* **[!UICONTROL Taken into account in campaign ROI calculation]**: takes the hypothesis result into account in the ROI calculation for the related campaign.

### Hypothesis template execution settings {#hypothesis-template-execution-settings}

The template's **[!UICONTROL General]** tab also lets you specify the hypothesis execution parameters. The options available are as follows:

* **[!UICONTROL Schedule execution for a time of low activity]**: lets you schedule the hypothesis launch to optimize Adobe Campaign performances. When this option is checked, the processing workflow on campaigns executes hypothesis calculation during downtime.

  ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**: level applied to the hypothesis to space out the hypothesis calculation orders if there are simultaneous executions.

  ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**: if necessary, lets you schedule hypothesis recalculation (for example, if you want to update indicators regularly until the end of the delivery). 

  ![](assets/response_exec_settings_001.png)

  To specify a schedule, apply the following process:

    1. Click the **[!UICONTROL Frequency of execution...]** link, then the **[!UICONTROL Change...]** button. 
    
       ![](assets/response_frequency_execution_001.png)

    1. Configure the frequency, the related events and the validity period.
    
       ![](assets/response_frequency_execution_002.png)

    1. Click **[!UICONTROL Finish]** to save the schedule.
    
       ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**: this function is reserved for expert users. It lets you add a tab to the measuring hypothesis audit to show SQL queries. This enables the detection of possible malfunctions if a simulation finishes with errors.
* **[!UICONTROL Keep execution workflow]**: lets you keep the workflow that was automatically generated at the start of the hypothesis calculation. In the hypotheses created from a template that has this option checked, the generated workflow is available to follow the process.

  >[!CAUTION]
  >
  >This option must be activated for debugging purposes only, in case of error while running the hypothesis.   
  >In addition, workflows generated automatically must not be modified. Any eventual modification would not be taken into account elsewhere for later calculations.  
  >If you have checked this option, delete the workflow after it has executed.

### Transactions {#transactions}

This tab contains the various fields and tables which let you save the history of recipient reactions in terms of transactions. Refer to the [Configuration](../../configuration/using/about-schema-reference.md) guide for more information on the tables dedicated to response management.

* **[!UICONTROL Schema (reaction log storage)]**: select the recipient reaction table. The out-of-the-box table in Adobe Campaign is **NmsRemaMatchRcp**.
* **[!UICONTROL Transaction schema]**: choose the table that the hypotheses will concern, i.e. the transaction or the purchase table.
* **[!UICONTROL Querying schema]**: choose the criteria for filtering the hypothesis. 
* **[!UICONTROL Link to individuals]**: choose the link between individuals and the table used as a transaction schema.
* **[!UICONTROL Link to the household]**: select the link to the household in the transactions schema if you wish to include all members of a household in a hypothesis. This field is optional.
* **[!UICONTROL Transaction date]**: this field is optional but recommended since it lets you define a scope for hypothesis calculation. 
* **[!UICONTROL Measurement period]**: lets you configure start and end dates during which hypotheses are executed and purchase lines are recovered.

  When the hypothesis is linked to a delivery, measurement is automatically triggered a few days after the contact date for direct mail deliveries, or after the delivery date for email or SMS deliveries.

  ![](assets/response_measurement_001.png)

  If the hypothesis is launched on the fly, it can be forced if would like to trigger it immediately. Otherwise, it is triggered automatically based on the configured end of calculation date, which is based on the hypothesis creation date (refer to [Creating a hypothesis on the fly on a delivery](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaction/Margin amount]**: these fields are optional and enable you to calculate turnover indicators automatically (refer to [Indicators](../../campaign/using/hypothesis-tracking.md#indicators)).
* **[!UICONTROL Unit amount]**: lets you set an amount for calculating revenue (refer to [Indicators](../../campaign/using/hypothesis-tracking.md#indicators)). 

  ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**: lets you specify additional reporting measures or axes from fields in the different tables.
* **[!UICONTROL Update offer proposition status]**: lets you change the status of the offer proposition if an offer recipient is identified by the hypothesis. 

  ![](assets/response_offer_status_001.png)

### Hypothesis perimeter {#hypothesis-perimeter}

Once you have defined the transaction table and the fields which the hypothesis will concern, you can refine the scope of your hypotheses by specifying the targeted transactions and deliveries using filters. You can also use a JavaScript script to explicitly point to a product referenced in the transaction table.

* **Filtering on transactions**: in the **[!UICONTROL Scope]** tab, you can configure a filter on the hypothesis. To do this:

    1. Click the **[!UICONTROL Edit query]** link.
    
       ![](assets/response_scope_filtering_001.png)

    1. Specify your filtering conditions.
    
       ![](assets/response_scope_filtering_002.png)

    1. Select the transaction which the hypothesis will concern.
    
       ![](assets/response_scope_filtering_003.png)

* **Filter on recipients**: in the **[!UICONTROL Scope]** tab, you can limit your hypothesis to any information linked to a message (delivery, recipient, email address, service, etc.):

    1. Click the **[!UICONTROL Add a filter]** link, then **[!UICONTROL Edit query]**.
    
       ![](assets/response_scope_filtering_004.png)

    1. Specify your filtering conditions.
    
       ![](assets/response_scope_filtering_005.png)

    1. Click **[!UICONTROL Finish]** to save your query.
    
       ![](assets/response_scope_filtering_006.png)

* **Script**: you can use a JavaScript script to dynamically overload the hypothesis settings during its execution.

  To do this, click the **[!UICONTROL Advanced settings]** link then enter the desired script.

  >[!NOTE]
  >
  >This option is for expert users.

  ![](assets/response_hypothesis_model_creation_011.png)

## Example: creating a hypothesis template on a delivery {#example--creating-a-hypothesis-template-on-a-delivery}

In this example, we are going to create a hypothesis template on a direct mail type delivery. The transaction table (**Purchases** in our example) which the hypotheses will be based on contains purchase lines linked to articles or products. We want to configure our model to create hypotheses on articles or products in the purchase table.

1. In the Adobe Campaign explorer, go to the **[!UICONTROL Resources > Templates > Hypothesis templates]** node.
1. Click **[!UICONTROL New]** to create a template.

   ![](assets/response_hypothesis_model_example_001.png)

1. Change the template label.

   ![](assets/response_hypothesis_model_example_002.png)

1. Select **[!UICONTROL Deliveries]** as a hypothesis type.
1. Specify that the delivery can contain a control group by checking the relevant box.
1. Choose the **[!UICONTROL Direct mail]** channel.

   >[!NOTE]
   >
   >Since the template is specific to direct mail deliveries, hypotheses created using this model may not be linked to any other delivery types.

1. In the **[!UICONTROL Transactions]** tab, select the recipient reactions table.

   ![](assets/response_hypothesis_model_example_006.png)

1. In the **[!UICONTROL Transactions schema]** field, choose your purchase table.

   ![](assets/response_hypothesis_model_example_007.png)

1. Select purchase lines in the **[!UICONTROL Querying schema]** field.

   ![](assets/response_hypothesis_model_example_008.png)

1. Choose the recipients linked to the purchase table.

   ![](assets/response_hypothesis_model_example_009.png)

1. Select the field linked to the purchase date.

   This lets you define a time frame for hypotheses. This stage isn't mandatory but it is recommended.

   ![](assets/response_hypothesis_model_example_010.png)

1. Configure the calculation period for 5 to 25 days.

   ![](assets/response_hypothesis_model_example_005.png)

1. In the **[!UICONTROL Scope]** tab, click **[!UICONTROL Edit query]** to create a filter on hypotheses.

   ![](assets/response_hypothesis_model_example_011.png)

   The template created thus enables you to run hypotheses on the products or articles in the purchase table.

1. Click **[!UICONTROL Save]** to record your template.
