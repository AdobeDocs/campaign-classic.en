---
title: Delivery
seo-title: Delivery
description: Delivery
seo-description: 
page-status-flag: never-activated
uuid: 8dd4c9d2-407a-44ac-a6c6-1c96b101e4d6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 48cfc7f4-65a7-494f-a17e-ff19ee7c8c15
index: y
internal: n
snippet: y
---

# Delivery{#delivery}

A **Delivery**-type activity lets you create a delivery action. It can be constructed using input elements.

To configure it, edit the activity and enter the delivery options.

![](assets/edit_diffusion.png)

1. **Delivery**

   You can:

    * Act on the delivery specified in the inbound transition. To do this, select the first option of the **Delivery** section of the window.

      This option can be used when a previous workflow activity has already created or specified the delivery. This can have been done, like in the example below, by an activity of the same type having generated an outbound transition.

      In the following example, the delivery is created for the first time. The population and the content are defined later. Next, the information for these three elements is re-entered into a new delivery activity using the inbound transition so that this can be sent.
    
      ![](assets/specified_transition_option_exemple.png)

    * Directly select the delivery concerned. To do this, select the **Explicit** option and select the delivery from the drop-down list of the **Delivery** field.

      The list shows unfinished deliveries contained in the **Deliveries** folder by default. To access other campaigns, click the **Select link** icon.
    
      ![](assets/diffusion_edit_1.png)

      Select the campaign from the drop-down list of the **Folder** field, or click **Display sub-levels** to display all of the deliveries contained in sub-folders:
    
      ![](assets/diffusion_edit_2.png)

      After selecting the delivery action, you can display the content by clicking the **Edit link** icon.
    
    * Create a script to calculate the delivery. To do this, select the **Calculated by a script** option and enter the script. You can open an input window by clicking the **Edit...** option. The following example recovers the identifier of the delivery:
    
      ![](assets/diffusion_edit_3.png)

    * Create a new delivery. To do this, select the **New, created from a template** option and select the delivery template which the delivery will be based on.
    
      ![](assets/diffusion_edit_4.png)

      Click the **Select link** icon to browse the folders, and click the **Edit link** icon if you wish to view the content of the selected template.

1. **Recipients**

   Recipients can be specified by the inbound events, for example following a file import, or specified in the delivery action. They can also be stored in one or more files.

   ![](assets/diffusion_edit_5.png)

1. **Content**

   The content of the message can be defined in the delivery or the inbound event.

   ![](assets/diffusion_edit_6.png)

1. **Action to execute**

   You can create the delivery, prepare it, start it, estimate the target or send a proof. 

   ![](assets/diffusion_edit_7.png)

   Select the type of action to be carried out:

    * **Save**: this option lets you create the delivery and save it. It will not analyze or deliver it.
    * **Estimate the target**: this option lets you calculate the delivery target to assess its potential (first analysis phase). This action is the equivalent of selecting the **Estimate the population to be targeted** option and clicking **Analyze** when sending a delivery to the main target via **Delivery**.
    * **Prepare**: this option lets you run the full analysis process (target calculation and content preparation). The delivery isn't sent. This action is the equivalent of selecting the **Deliver as soon as possible** option and clicking **Analyze** when sending a delivery to the main target with **Delivery**.
    * **Send a proof**: this option lets you send a proof of the delivery. This action is the equivalent of clicking the **Send a proof** button in the toolbar of a delivery with **Delivery** 
    * **Prepare and start**: this option launches the full analysis process (target calculation and content preparation) and sends the delivery. This action is the equivalent of clicking **Deliver as soon as possible**, **Analyze**, and **Confirm delivery** option when sending a delivery to the main target with **Delivery**.

   The **Act on a delivery** activity used further on in the workflow lets you launch all remaining steps required for starting the delivery (target calculation, content preparation, delivery). For more on this, refer to [Delivery control](../../workflow/using/delivery-control.md).

   The following options are also available:

    * **Generate an outbound transition**

      Creates an outbound transition that will be activated at the end of execution. You can choose whether or not to retrieve the target of the outbound delivery.
    
    * **Do not recover target**

      Does not recover the target of the outgoing delivery action.
    
    * **Processing errors**

      Refer to [Delivery control](../../workflow/using/delivery-control.md).

   The **Script** tab lets you modify the delivery parameters.

   ![](assets/edit_diffusion_fil_script.png)

## Example: delivery workflow {#example--delivery-workflow}

Create a new workflow and add activities as shown in the graphic below:

![](assets/new-workflow-5.png)

Open the **Delivery** activity and define the properties as follows:

* In the **Delivery** section, select **New, created from a template** and select a delivery template. 
* In the **Recipients** section, select **Specified in the delivery**. 
* In the **Action to execute** section, keep the **Prepare** option.

![](assets/new-workflow-param-delivery.png)

Click **OK** to close the properties window. You have just configured an activity that consists of creating and preparing a new delivery based on a delivery template whose target will be specified within it.

Open the **Approval** activity and define the properties as follows:

1. In the **Assignment type** field, select a group in which you are registered. If you are connected using the 'admin' account, select the Administration group.
1. Next, enter a title and insert the following text in the message body:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   This is a message that includes an expression written in JavaScript: **vars.recCount** represents the number of recipients targeted by the delivery of the preceding task. For further information on JavaScript expressions, refer to [JavaScript scripts and templates](../../workflow/using/javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   The Approval task is detailed in [Approval](../../workflow/using/approval.md).

## Input parameters {#input-parameters}

Delivery identifier, if the **Specified in the transition** option is selected in the **Delivery** section.

* deliveryId
* tableName
* schema

Each inbound event must specify a target defined by these parameters.

>[!NOTE]
>
>This parameter only appears if the **Specified by inbound event(s)** option is selected in the **Recipients** section.

* filename

  Full name of the file generated if the **File(s) specified by inbound event(s)** option is selected in the **Recipients** section.

* contentId

  Content identifier if the **Specified by inbound events** option is selected in the **Content** section.

## Output parameters {#output-parameters}

* tableName
* schema
* recCount

This set of three values identifies the target resulting from the delivery. **tableName** is the name of the table which memorizes the identifiers of the target,** schema **is the schema of the population (usually nms:recipient) and **recCount** is the number of elements in the table.

The transition associated with the complement has the same parameters.

>[!NOTE]
>
>There are no output parameters when the **Do not recover target** option is selected.

