---
solution: Campaign Classic
product: campaign
title: Updating data
description: Updating data
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
---
# Update data{#updating-data}

The data linked to a recipient's profile can be updated manually or automatically.

## Set up an automatic update {#setting-up-an-automatic-update}

An automatic update can be configured via a workflow. For more on this, refer to [this section](../../workflow/using/update-data.md).

## Perform a mass update {#performing-a-mass-update}

To perform manual updates, right-click the selected recipient(s) to use the **[!UICONTROL Actions]** shortcut menu, or use the **[!UICONTROL Actions]** icon.

![](assets/s_ncs_user_action_icon.png)

There are two types of updates: mass update for a set of recipients, and data merging between two profiles. For each action, a wizard lets you configure the update.

### Mass update {#mass-update}

For mass updating, use **[!UICONTROL Action > Mass update of selected lines...]**. The wizard helps you configure and run the update.

The first step of the wizard is to specify the field(s) to be updated.

The left-hand section of the wizard displays the list of available fields. Use the **[!UICONTROL Find]** field to run a search of these fields. Press the **Enter** key to browse the list. The field names matching your entry appear in bold, as shown below.

Double-click the field(s) to be updated to display them in the right-hand section of the wizard.

![](assets/s_ncs_user_update_wizard01_1.png)

In the event of an error, use the **[!UICONTROL Delete]** button to delete a field from the list of fields to be updated.

Select or enter the values to apply to the profiles to be updated.

![](assets/s_ncs_user_update_wizard01_12.png)

You can click **[!UICONTROL Distribution of values]** to display the distribution of values of the selected field for the recipients present in the current folder (not only the recipients affected by the update).

![](assets/s_ncs_user_update_wizard01_2.png)

You can define filters to display the distribution of values in this window or modify the current folder to display the distribution of values in another folder. These are read-only actions; they do not affect the configuration of the update being defined.

![](assets/s_ncs_user_update_wizard01_3.png)

Close this window and click **[!UICONTROL Next]** to display the second update wizard step. In this step, you can launch the update by clicking **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

Information concerning update execution is displayed in the upper section of the wizard.

The **[!UICONTROL Stop]** lets you cancel the update, but certain records might have been updated, and stopping the process will not cancel these updates. The progress bar shows how far the operation has advanced.

### Merge data {#merge-data}

Select **[!UICONTROL Merge selected lines...]** to launch the merging of two recipient profiles. The profiles to be merged must be selected before selecting the option. The merge is configured and launched using a wizard.

The wizard displays the values to be retrieved for each field completed in one or other of the source profiles. If one or more fields in the profiles to be merged have different values, they are displayed in the **[!UICONTROL List of conflicts]** section. You can then select the default profile using the radio buttons under the list, as in the following example:

![](assets/s_ncs_user_merge_wizard01_1.png)

Click **[!UICONTROL Compute]** to display the result of your choice.

![](assets/s_ncs_user_merge_wizard01_2.png)

Check the **[!UICONTROL Result]** columns of both sections of the window, and click **[!UICONTROL Finish]** to run the merge.

## Export data {#exporting-data}

The content of a list can be exported. To configure and run the export:

1. Select records to export.
1. Right-click and select **[!UICONTROL Export...]**.

    ![](assets/s_ncs_user_export_list.png)

1. Then select the data to extract. By default, all columns displayed are added to the output columns.

    ![](assets/s_ncs_user_export_list_start.png)

   For more on how to configure the export wizard, refer to [this section](../../platform/using/executing-export-jobs.md).

## Subscribe to a service {#subscribing-to-a-service}

In most cases, recipients subscribe to a newsletter through a dedicated landing page, as explained in [this section](../../delivery/using/managing-subscriptions.md). However, the profiles of filtered recipients can be subscribed to a service (Newsletter or Viral service) manually. To do this:

1. Select the recipients you want to subscribe and right-click. 
1. Select **[!UICONTROL Actions > Subscribe selection to a service]**.

    ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Select the desired service and click **[!UICONTROL Next]**:

    ![](assets/s_ncs_user_selection_subscribe_service_2.png)

    >[!NOTE]
    >
    >This editor lets you create a new service: click the **[!UICONTROL Create]** button.

1. You can **[!UICONTROL Send a confirmation message]** to recipients. The content of this message can be configured in the subscription scenario linked to the selected service.
1. Click the **[!UICONTROL Start]** button to run the subscription process.

    ![](assets/s_ncs_user_selection_subscribe_service_3.png)

The upper section of the window lets you monitor the execution process. The **[!UICONTROL Stop]** button lets you stop the process. However, recipients already processed will be subscribed.

If you uncheck the **[!UICONTROL Do not keep a trace of this job in the database]** option, you can select (or create) the execution folder where the information on this process will be stored.

To check on the process, go to the **[!UICONTROL Subscriptions]** tab on the profiles of the recipients concerned by this operation, or to the **[!UICONTROL Subscriptions]** tab accessed via the **[!UICONTROL Profiles and Targets > Services and Subscriptions]** node.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>For more on creating and configuring information services, refer to [this page](../../delivery/using/managing-subscriptions.md).
