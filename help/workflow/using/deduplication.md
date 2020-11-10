---
title: Deduplication
description: Learn more about the Deduplication workflow activity
page-status-flag: never-activated
uuid: 90dee589-ac45-442e-89ef-1c14bb22200d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 83b915bd-7e23-41b5-9f9a-f7eb72026376
---

# Deduplication{#deduplication}

Deduplication deletes duplicates from the results of inbound activities. Deduplication can be performed on the email address, telephone number, or another field.

## Best practices {#best-practices}

During deduplication, inbound flows are processed separately. If for instance recipient A is found in the result of query 1 as well as in the result of query 2, they will not be deduplicated.

This issue needs to be addressed as follows:

* Create a **Union** activity to unify each inbound flow.
* Create a **Deduplication** activity after the **Union** activity.

![](assets/dedup_bonnepratique.png)

## Configuration {#configuration}

To configure a deduplication, enter its label, the method, and the deduplication criteria, and the options concerning the result.

Click the **[!UICONTROL Edit configuration...]** link to define the deduplication mode.

![](assets/s_user_segmentation_dedup_param.png)

1. Target selection

   Select the type of target for this activity (by default, deduplication concerns recipients) and the criterion to be used, i.e. the field for which identical values enable you to identify duplicates: email address, mobile or telephone number, fax number or direct mail address. 

   ![](assets/s_user_segmentation_dedup_param2.png)

   >[!NOTE]
   >
   >If you are using external data as input, for example from an external file, make sure you select the **[!UICONTROL Temporary schema]** option.
   >
   >In the next step, the **[!UICONTROL Other]** option lets you select the criterion or criteria to be used:

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Deduplication methods

   From the drop-down list, select the deduplication method to be used, and enter the number of duplicates to be kept.

   ![](assets/s_user_segmentation_dedup_param4.png)

   The following methods are available:

    * **[!UICONTROL Choose for me]**: randomly selects the record to be kept out of the duplicates.
    * **[!UICONTROL Following a list of values]**: lets you define a value priority for one or more fields. To define the values, select a field or create an expression, then add the value(s) into the appropriate table. To define a new field, click the **[!UICONTROL Add]** button located above the list of values.
    
      ![](assets/s_user_segmentation_dedup_param5.png)

    * **[!UICONTROL Non-empty value]**: this lets you keep records for which the value of the selected expression is not empty as a priority.
    
      ![](assets/s_user_segmentation_dedup_param6.png)

    * **[!UICONTROL Using an expression]**: lets you keep records with the lowest (or highest) value of the given expression. 
    
      ![](assets/s_user_segmentation_dedup_param7.png)

   Click **[!UICONTROL Finish]** to approve the selected deduplication method.

   The middle section of the window summarizes the defined configuration.

   In the lower section of the activity editor window, you can modify the label for the outbound transition of the graphical object and enter a segment code that will be associated with the result of the activity. This code can later be used as a targeting criterion.

   ![](assets/s_user_segmentation_dedup_param8.png)

   Check the **[!UICONTROL Generate complement]** option if you wish to exploit the remaining population. The complement consists of all the duplicates. An additional transition will then be added to the activity, as follows:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Example: Identify the duplicates before a delivery {#example--identify-the-duplicates-before-a-delivery}

In the following example, the deduplication concerns the union of three queries.

The aim of the workflow is to define the target for a delivery by excluding duplicates to avoid sending it to the same recipient several times.

The identified duplicates will also be integrated into a dedicated duplicates list that can be reused if necessary.

![](assets/deduplication_example.png)

1. Add and link the various activities required for the workflow to operate as shown above.

   The union activity is used here to "unify" the three queries into one single transition. Thus, deduplication will not work for each query individually but for the whole of the query. For more on this subject, refer to [Best practices](#best-practices).

1. Open the deduplication activity then click the **[!UICONTROL Edit configuration...]** link to define the deduplication mode.
1. In the new window, select **[!UICONTROL Database schema]**.
1. Select **Recipients** as targeting and filtering dimensions.
1. Select the ID field for the **[!UICONTROL Email]** duplicates, to send the delivery only once to every email address, then click **[!UICONTROL Next]**.

   If you wish to base the duplicate IDs on a specific field, select **[!UICONTROL Other]** to access the list of available fields.

1. Choose to keep only one entry when the same email address is identified for multiple recipients.
1. Select the **[!UICONTROL Choose for me]** deduplication mode so that the records saved in case of identified duplicates are randomly chosen, then click **[!UICONTROL Finish]**.

When running the workflow, all recipients identified as duplicates are excluded from the result (and therefore the delivery) and added to the duplicates list. This list may be used again rather than having to re-identify the duplicates.

## Input parameters {#input-parameters}

* tableName
* schema

Each inbound event must specify a target defined by these parameters.

## Output parameters {#output-parameters}

* tableName
* schema
* recCount

This set of three values identifies the target resulting from the deduplication. **[!UICONTROL tableName]** is the name of the table which saves target identifiers, **[!UICONTROL schema]** is the schema of the population (usually nms:recipient) and **[!UICONTROL recCount]** is the number of elements in the table.

The transition associated with the complement has the same parameters.
