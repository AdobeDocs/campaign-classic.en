---
solution: Campaign Classic
product: campaign
title: CRM Connectors data synchronization
description: Manage data between Campaign and your CRM
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
---
# Synchronize data between Campaign and the CRM {#data-synchronization}

Data synchronization between Adobe Campaign and the CRM is carried out via a dedicated workflow activity: [CRM connector](../../workflow/using/crm-connector.md).

For example, to import the Microsoft Dynamics data into Adobe Campaign, create the following type of workflow:

![](assets/crm_connectors_msdynamics_07.png)

This workflow imports the contacts via Microsoft Dynamics, synchronizes them with the existing Adobe Campaign data, deletes duplicate contacts, and updates the Adobe Campaign database.

The **[!UICONTROL CRM Connector]** activity needs to be configured to synchronize data.

![](assets/crm_connectors_msdynamics_08.png)

With this activity you can:

* Import from the CRM - [Learn more](#importing-from-the-crm)
* Export to CRM - [Learn more](#exporting-to-the-crm)
* Import objects deleted in the CRM - [Learn more](#importing-objects-deleted-in-the-crm)
* Delete objects in the CRM - [Learn more](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Select the external account that matches the CRM that you want to configure synchronization with, then select the object to be synchronized: accounts, opportunities, leads, contacts, etc.

![](assets/crm_task_select_obj.png)

The configuration of this activity depends on the process to be carried out. Various configurations are detailed below.

## Import from the CRM {#importing-from-the-crm}

To import data via the CRM in Adobe Campaign, you need to create the following type of workflow:

![](assets/crm_wf_import.png)

For an import activity, the **[!UICONTROL CRM Connector]** activity configuration steps are:

1. Select an **[!UICONTROL Import from the CRM]** operation.
1. Go to the **[!UICONTROL Remote object]** drop-down list and select the object concerned by the process. This object coincides with one of the tables created in Adobe Campaign during connector configuration.
1. Go to the **[!UICONTROL Remote fields]** section and enter the fields to be imported.

   To add a field, click the **[!UICONTROL Add]** button in the toolbar, then click the **[!UICONTROL Edit expression]** icon.

   ![](assets/crm_task_import_add_field.png)

   If necessary, alter the data format via the drop-down list of the **[!UICONTROL Conversion]** columns. Possible conversion types are detailed in [Data format](#data-format).

   >[!IMPORTANT]
   >
   >The identifier of the record in the CRM is mandatory for linking objects in CRM and in Adobe Campaign. It is added automatically when the box is approved.  
   >
   >The last modification date on the CRM side is also mandatory for incremental data imports.

1. You can also filter the data to be imported based on your needs. To do this, click the **[!UICONTROL Edit the filter...]** link.

   In the following example, Adobe Campaign will only import contacts for which some activity has been recorded since Nov 1st 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >The limitations linked to data filtering modes are detailed in [Filtering data](#filtering-data).

1. The **[!UICONTROL Use automatic index...]** option enables you to automatically manage incremental object synchronization between the CRM and Adobe Campaign, depending on the date and their last modification.

   For more on this, refer to [Variable management](#variable-management).

### Manage variables {#variable-management}

Enable the **[!UICONTROL Automatic index]** option to collect only objects modified since the last import.

![](assets/crm_task_import_option.png)

The date of the last synchronization is stored in an option specified in the configuration window, by default: **LASTIMPORT_<%=instance.internalName%>_<%=activityName%>**.

>[!NOTE]
>
>This note only applies to the generic **[!UICONTROL CRM Connector]** activity. For other CRM activities, the process is automatic.  
>
>This option has to be manually created and populated under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. It must be a text option and its value needs to match the following format: **yyyy/MM/dd hh:mm:ss**. 
> 
>You need to manually update this option for any further import.

You can specify the remote CRM field to be taken into account to identify the most recent changes.

By default, the following fields are used (in the specified order):

* For Microsoft Dynamics: **modifiedon**,
* For Salesforce.com: **LastModifiedDate**, **SystemModstamp**.

Activating the **[!UICONTROL Automatic index]** option generates three variables that can be used in the synchronization workflow via a **[!UICONTROL JavaScript code]** type activity. These activities are:

* **vars.crmOptionName**: represents the name of the option that contains the last import date.
* **vars.crmStartImport**: represents the start date (included) of the last data recovery.
* **vars.crmEndDate**: represents the end date (excluded) of the last data recovery.

  >[!NOTE]
  >
  >These dates are shown in the following format: **yyyy/MM/dd hh:mm:ss**.

### Filter data {#filtering-data}

To ensure efficient operation with the various CRMs, filters need to be created using the following rules:

* Each filtering level may only use one type of operator.
* The AND NOT operator is not supported.
* Comparisons may only concern null values ('is empty'/'is not empty' type) or numbers. This means that the value (right-hand column) is assessed and the result of this assessment must be a number. JOIN type comparisons are therefore not supported.
* The value contained in the right-hand column is assessed in JavaScript.
* JOIN comparisons are not supported.
* The expression in the left-hand column must be a field. It cannot be a combination of several expressions, a number, etc.

For example, the following filtering conditions will NOT be valid for a CRM import, because the OR operator is placed at the same level as the AND operators:

* The OR operator is placed at the same level as the AND operators
* Comparisons are carried out on text strings

![](assets/crm_import_wrong_filter.png)

### Order by {#order-by}

In Microsoft Dynamics and Salesforce.com, you can sort the remote fields to be imported in ascending or descending order.

To do this, click the **[!UICONTROL Order by]** link and add the columns to the list.

The order of the columns in the list is the sorting order:

![](assets/crm_import_order.png)

### Record identification {#record-identification}

Rather than import elements included (and possibly filtered) in the CRM, you can use a population calculated beforehand in the workflow.

To do this, select the **[!UICONTROL Use the population calculated upstream]** option and specify the field that contains the remote identifier.

Then select the fields of the inbound population that you want to import, as shown below:

![](assets/crm_wf_import_calculated_population.png)

## Exporting to the CRM {#exporting-to-the-crm}

Exporting Adobe Campaign data into the CRM lets you copy entire contents to a CRM database.

To export data towards the CRM, you need to create the following type of workflow:

![](assets/crm_export_diagram.png)

For an export, apply the following configuration to the **[!UICONTROL CRM Connector]** activity:

1. Select an **[!UICONTROL Export to CRM]** operation.
1. Go to the **[!UICONTROL Remote object]** drop-down list and select the object concerned by the process. This object coincides with one of the tables created in Adobe Campaign during connector configuration.

   >[!IMPORTANT]
   >
   >The export function of the **[!UICONTROL CRM Connector]** activity can insert or update fields on the CRM side. To enable field updates in the CRM, you need to specify the primary key of the remote table. If the key is missing, data will be inserted (instead of being updated).

1. In the **[!UICONTROL Mapping]** section, specify the fields to be exported and their mapping in the CRM.

   ![](assets/crm_export_config.png)

   To add a field, click the **[!UICONTROL Add]** button in the toolbar, then click the **[!UICONTROL Edit expression]** icon.

   >[!NOTE]
   >
   >For a given field, if no match is defined on the CRM side, the values cannot be updated: they are inserted directly into the CRM.

   If necessary, alter the data format via the drop-down list of the **[!UICONTROL Conversion]** columns. Possible conversion types are detailed in [Data format](#data-format).

   >[!NOTE]
   >
   >The list of records to be exported and the result of the export are saved in a temporary file that remains accessible until the workflow is finished or re-started. This enables you to start the process again in case of errors without running the risk of exporting the same record several times or losing data.

## Additional configurations {#additional-configurations}

### Data format {#data-format}

You can convert data format on the fly when importing them to or from the CRM.

To do this, select the conversion to be applied in the matching column.

![](assets/crm_task_import.png)

The **[!UICONTROL Default]** mode applies automatic data conversion, which in most cases equals a copy/paste of the data. However, time zone management is applied.

Other possible conversions are:

* **[!UICONTROL Date only]**: this mode deletes Date + Time type fields.
* **[!UICONTROL Without time offset]**: this mode cancels the time zone management applied in the default mode.
* **[!UICONTROL Copy/Paste]**: this mode uses raw data such as strings (no conversion).

### Error processing {#error-processing}

Within the framework of data imports or exports, you can apply a specific process to errors and rejects. To do this, select the **[!UICONTROL Process rejects]** and **[!UICONTROL Process errors]** options in the **[!UICONTROL Behavior]** tab.

![](assets/crm_export_options.png)

These options place the matching output transitions.

![](assets/crm_export_transitions.png)

Then place the activities relevant to the processes you want to apply.

To process errors for instance, you can add a wait box and schedule retries.

Rejects are collected with their error code and the related message, this means you can set up the tracking of rejects to optimize your synchronization process.

>[!NOTE]
>
>Even when the **[!UICONTROL Process rejects]** option isn't enabled, a warning is generated for each rejected column with an error code and message.

The **[!UICONTROL Reject]** output transition lets you access the output schema that contains the specific columns relevant to error messages and codes. For Salesforce.com, this column is **errorSymbol** (error symbol, different from the error code), **errorMessage** (description of the error context).

## Import objects deleted in the CRM {#importing-objects-deleted-in-the-crm}

To enable the setting up of an extensive data synchronization process, you can import objects deleted in the CRM into Adobe Campaign.

To do this, apply the following steps:

1. Select an **[!UICONTROL Import objects deleted in the CRM]** operation.
1. Go to the **[!UICONTROL Remote object]** drop-down list and select the object concerned by the process. This object coincides with one of the tables created in Adobe Campaign during connector configuration.
1. Specify the deletion period to be taken into account in the **[!UICONTROL Start date]** and the **[!UICONTROL End date]** fields. These dates will be included in the period.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >The element deletion period must coincide with the limitations specific to the CRM. This means that for Salesforce.com, for instance, elements deleted over 30 days ago cannot be recovered.

## Delete objects in the CRM {#deleting-objects-in-the-crm}

To delete objects on the CRM side, you need to specify the primary key of the remote elements to be deleted.

![](assets/crm_delete_in_crm.png)

The **[!UICONTROL Behavior]** tab lets you enable the processing of rejects. This option generates a second output transition for the **[!UICONTROL CRM connector]** activity. For more on this, refer to [Error processing](#error-processing).

>[!NOTE]
>
>Even when the **[!UICONTROL Process rejects]** option is disabled, a warning is generated for each rejected column.
>
