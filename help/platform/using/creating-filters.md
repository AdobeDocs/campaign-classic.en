---
product: campaign
title: Creating filters
description: Creating filters
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
---
# Create filters{#creating-filters}

When you navigate in the Adobe Campaign tree (from the **[!UICONTROL Explorer]** menu in the home page), the data contained in the database is displayed in lists. These lists can be configured to display only the data required by the operator. Actions can then be launched on the filtered data. Filter configuration lets you select data from a list **[!UICONTROL dynamically]**. If the data is modified, the filtered data is updated.

>[!NOTE]
>
>User interface configuration settings are defined locally at the device level. It may sometimes be necessary to clean up this data, particularly if problems arise when refreshing data. To do this, use **[!UICONTROL File > Clear the local cache]** menu.

## Typology of available filters {#typology-of-available-filters}

Adobe Campaign lets you apply filters to data lists.

These filters can be used once, or you can save them for future use. You can apply several filters at the same time.

The following filter types are available in Adobe Campaign:

* **Default filters**

  The **default filter** is accessible via the fields located above the lists. It lets you filter on predefined fields (for recipient profiles, these are the name and email address by default). You can use the fields to enter the characters to filter on or to selection the filter conditions from a drop-down list.

  ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an e-mail address in the domain "yahoo.com".
-->
  You can change the default filter of a list. For more on this, refer to [Change the default filter](#altering-the-default-filter).

* **Simple filters**

  **Simple filters** are one-off filters on the columns. They are defined with one or more simple search criteria on the displayed columns.

  You can combine several simple filters on the same data list to refine your search. The filter fields are displayed one beneath the other. They can be deleted independently of each other.

  ![](assets/filters_recipient_simple_filter.png)

  Simple filters are detailed in [Create a simple filter](#creating-a-simple-filter).

* **Advanced filters**

  **Advanced filters** are created using a query or a combination of queries on the data.

  For more on creating an advanced filter, refer to [Create an advanced filter](#creating-an-advanced-filter).

  You can use functions to define the content of the filter. For more on this, refer to [Create an advanced filter with functions](#creating-an-advanced-filter-with-functions).

  >[!NOTE]
  >
  >For more on building queries in Adobe Campaign, refer to [this section](../../platform/using/about-queries-in-campaign.md).

* **User filters**

  An **application filter** is an advanced filter that has been saved, to use and share its configuration with the other operators.

  The **[!UICONTROL Filters]** button located above the lists offers a set of application filters that can be combined to refine the filtering. The method for creating these filters is presented in [Save a filter](#saving-a-filter).

## Change the default filter {#altering-the-default-filter}

To change the default filter for a recipient list, click the **[!UICONTROL Profiles and Targets > Pre-defined filters]** node of the tree.

For all other types of data, configure the default filter via the **[!UICONTROL Administration > Configuration > Predefined filters]** node.

Apply the following steps:

1. Select the filter you want to be used by default.
1. Click the **[!UICONTROL Parameters]** tab and select **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >If a default filter is already applied to the list, you need to disable it before applying a new filter. To do this, click the red cross to the right of the filtering fields.

1. Click **[!UICONTROL Save]** to apply the filter.

   >[!NOTE]
   >
   >The filter definition window is detailed in [Create an advanced filter](#creating-an-advanced-filter) and [Save a filter](#saving-a-filter).

## Create a simple filter {#creating-a-simple-filter}

To create a **simple filter**, apply the following steps:

1. Right-click the field you want to filter and select **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   The default filter fields are displayed above the list.

1. Select the filter option from the drop-down list, or enter the filter criteria to apply (the method for selecting or entering criteria depends on the type of field: text, enumerated, etc.).

   ![](assets/s_ncs_user_sort_fields.png)

1. To activate the filter, press Enter on the keyboard, or click the green arrow to the right of the filter fields.

If the field on which you want to filter the data is not displayed in the form of the profile, you can add it in the columns displayed, then filter on that column. To do this,

1. Click the **[!UICONTROL Configure the list]** icon.

   ![](assets/s_ncs_user_configure_list.png)

1. Select the column to be displayed, for example the age of the recipients.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Right-click the **Age** column in the recipient list, and select **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   You can then select the age filtering options.

   ![](assets/s_ncs_user_delete_filter.png)

## Create an advanced filter {#creating-an-advanced-filter}

To create an **advanced filter**, apply the following steps:

1. Click the **[!UICONTROL Filters]** button and select **[!UICONTROL Advanced filter...]**. 

   ![](assets/filters_recipient_create_adv_filter.png)

   You can also right-click the list of data to filter and select **[!UICONTROL Advanced filter...]**.

   The filtering condition definition window is displayed.

1. Click the **[!UICONTROL Expression]** column to define the input value.
1. Click **[!UICONTROL Edit expression]** to select the field to which the filter will be applied.

   ![](assets/s_user_filter_choose_field.png)

1. From the list, select the field on which data will be filtered. Click **[!UICONTROL Finish]** to confirm.
1. Click the **[!UICONTROL Operator]** column and select the operator to be applied from the drop-down list.
1. Select an expected value from the **[!UICONTROL Value]** column. You can combine several filters to refine your query. To add a filter condition, click **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. You can assign a hierarchy to the expressions or change the order of the query expressions using the toolbar arrows.
1. The default operator between expressions is **And**, but you can change this by clicking the field. You can select an **Or** operator.

   ![](assets/s_ncs_user_filter_operator.png)

1. Click **[!UICONTROL OK]** to confirm filter creation and apply it to the list.

The filter applied is displayed above the list.

![](assets/s_ncs_user_filter_adv_edit.png)

To edit or modify this filter, click its label.

To cancel this filter, click the **[!UICONTROL Remove this filter]** icon to the right of the filter.

![](assets/s_ncs_user_filter_adv_remove.png)

You can save an advanced filter to keep it for future use. For further information about this type of filter, see [Save a filter](#saving-a-filter).

### Create an advanced filter with functions {#creating-an-advanced-filter-with-functions}

Advanced filters can use functions; **filters with functions** are created via an expression editor that lets you create formulas using the database data and advanced functions. To create a filter with functions, repeat advanced filter creation steps 1, 2 and 3, then proceed as follows:

1. In the field selection window, click **[!UICONTROL Advanced selection]**.
1. Select the type of formula to be used: aggregate, existing user filter or expression.

   ![](assets/s_ncs_user_filter_formula_select.png)

   The following options are available:

    * **[!UICONTROL Field only]** to select a field. This is the default mode. 
    * **[!UICONTROL Aggregate]** to select the aggregate formula to be used (counts, sum, average, maximum, minimum).
    * **[!UICONTROL User filter]** to select one of the existing user filters. User filters are detailed in [Save a filter](#saving-a-filter).
    * **[!UICONTROL Expression]** to access the expressions editor.

      The expression editor lets you define an advanced filter. It looks like this:
    
      ![](assets/s_ncs_user_create_exp_exple01.png)

      It lets you select fields in the database tables and attach advanced functions to them: Select the function to use in the **[!UICONTROL List of functions]**. The functions available are detailed in [List of functions](../../platform/using/defining-filter-conditions.md#list-of-functions). Next, select the field or fields concerned by the functions and click **[!UICONTROL OK]** to approve the expression.

      >[!NOTE]
      >
      >For an example of filter creation based on an expression, refer to [this section](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## Save a filter {#saving-a-filter}

Filters are specific to each operator and are re-initialized each time the operator clears the cache of their client console.

You can create an **application filter** by saving an advanced filter: it can be re-used by right-clicking in any list or via the **[!UICONTROL Filters]** button located above the lists.

These filters can also be accessed directly via the delivery wizard, in the target selection stage (refer to [this section](../../delivery/using/creating-an-email-delivery.md) for more on creating deliveries). To create the application filter, you can:

* Convert an advanced filter to an application filter. To do this, click **[!UICONTROL Save]** before closing the advanced filter editor.

  ![](assets/s_ncs_user_filter_save.png)

* Create this application filter via the **[!UICONTROL Administration > Configuration > Predefined filters]** (or **[!UICONTROL Profiles and targets > Predefined filters]** for recipients) node of the tree. To do this, right-click the list of filters, and select **[!UICONTROL New...]**. The procedure is the same as for creating advanced filters.

  The **[!UICONTROL Label]** field enables you to name this filter. This name will appear in the combo box of the **[!UICONTROL Filters...]** button. 

  ![](assets/user_filter_apply.png)

You can delete all filters on the current list by right-clicking and selecting **[!UICONTROL No filter]** or via the **[!UICONTROL Filters]** icon located above the list.  

You can combine filters by clicking the **[!UICONTROL Filters]** button and using the **[!UICONTROL And...]** menu.

![](assets/s_ncs_user_filter_combination.png)

## Filter recipients {#filtering-recipients}

Predefined filters (see [Save a filter](#saving-a-filter)) enable you to filter the profiles of recipients contained in the database. You can edit filters from the **[!UICONTROL Profiles and Targets > Predefined filters]** node of the tree. The filters are listed in the upper section of the workspace, via the **[!UICONTROL Filters]** button.

Select a filter to display its definition and to access a preview of the filtered data.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>For a detailed example of predefined filter creation, refer to [Use case](../../platform/using/use-case.md).

The predefined filters are:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Query</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Opened<br /> </td> 
   <td> Selects recipients who have opened a delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Opened but not clicked<br /> </td> 
   <td> Selects recipients who have opened a delivery but have not clicked on a link.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inactive recipients<br /> </td> 
   <td> Selects recipients who have not opened a delivery in X months.<br /> </td> 
  </tr> 
  <tr> 
   <td> Last activity by device type<br /> </td> 
   <td> Selects recipients who have clicked or opened delivery Y using device X in the last Z days.<br /> </td> 
  </tr> 
  <tr> 
   <td> Last activity by device type (Tracking)<br /> </td> 
   <td> Selects recipients who have clicked or opened delivery Y using device X in the last Z days.<br /> </td> 
  </tr> 
  <tr> 
   <td> Untargeted recipients<br /> </td> 
   <td> Selects recipients who have never been targeted via channel Y in X months.<br /> </td> 
  </tr> 
  <tr> 
   <td> Very active recipients<br /> </td> 
   <td> Selects recipients who have clicked in a delivery at least X times in the last Y months.<br /> </td> 
  </tr> 
  <tr> 
 <td> Denylisted email address<br /> </td> 
    <td> Selects recipients whose email address is on the denylist.<br/> </td>
  </tr> 
  <tr> 
   <td> Quarantined email address<br /> </td> 
   <td> Selects recipients whose email address is quarantined.<br /> </td> 
  </tr> 
  <tr> 
   <td> Email addresses duplicated in the folder<br /> </td> 
   <td> Selects recipients whose email address is duplicated in the folder.<br /> </td> 
  </tr> 
  <tr> 
   <td> Neither opened nor clicked<br /> </td> 
   <td> Selects recipients who have not opened a delivery, or clicked in a delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> New recipients (days)<br /> </td> 
   <td> Selects recipients that were created in the last X days.<br /> </td> 
  </tr> 
  <tr> 
   <td> New recipients (minutes)<br /> </td> 
   <td> Selects recipients that were created in the last X minutes.<br /> </td> 
  </tr> 
  <tr> 
   <td> New recipients (months)<br /> </td> 
   <td> Selects recipients that were created in the last X months.<br /> </td> 
  </tr> 
  <tr> 
   <td> By subscription<br /> </td> 
   <td> Selects recipients by subscription.<br /> </td> 
  </tr> 
  <tr> 
   <td> By clicking on a specific link<br /> </td> 
   <td> Selects recipients who clicked on a particular URL in a delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> By post delivery behavior<br /> </td> 
   <td> Selects recipients according to their behavior after receiving a delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> By creation date<br /> </td> 
   <td> Selects recipients by creation date, over a period ranging from X months (current date minus n months) to Y months (current date minus n months).<br /> </td> 
  </tr> 
  <tr> 
   <td> By list<br /> </td> 
   <td> Selects recipients by list.<br /> </td> 
  </tr> 
  <tr> 
   <td> By number of clicks<br /> </td> 
   <td> Selects recipients who clicked in a delivery in the last X months.<br /> </td> 
  </tr> 
  <tr> 
   <td> By number of messages received<br /> </td> 
   <td> Selects recipients according to the number of messages that they received.<br /> </td> 
  </tr> 
  <tr> 
   <td> By number of opens<br /> </td> 
   <td> Selects recipients who opened between X and Y deliveries over Z amount of time.<br /> </td> 
  </tr> 
  <tr> 
   <td> By name or email<br /> </td> 
   <td> Selects recipients according to their name or email.<br /> </td> 
  </tr> 
  <tr> 
   <td> By age range<br /> </td> 
   <td> Selects recipients according to their age.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>All comparisons concerning counting and periods are to be understood in the broader sense (recipients that correspond to the query limits are included in the comparison).

Examples of how the data is calculated:

* Selects recipients who are less than 30 years old: 

  ![](assets/predefined_filters_01.png)

* Selects recipients who are 18 years of age or older:

  ![](assets/predefined_filters_03.png)

* Selects recipients aged between 18 and 30:

  ![](assets/predefined_filters_02.png)

## Advanced settings for data filters {#advanced-settings-for-data-filters}

Click the **[!UICONTROL Settings]** tab to access the following options:

* **[!UICONTROL Default filter for the associated document type]**: this option lets you suggest this filter by default in the editor of the lists concerned by the sort.

  For example, the **[!UICONTROL By name or login]** filter is applied to operators. This option is selected, and so the filter is always offered on all operator lists.

* **[!UICONTROL Filter shared with other operators]**: this option lets you make the filter available to all the other operators on the current database.
* **[!UICONTROL Use parameter entry form]**: this option lets you define the filter field(s) to be displayed above the list when this filter is selected. These fields let you define the filter settings. This form must be entered in XML format via the **[!UICONTROL Form]** button. For example, the preconfigured filter **[!UICONTROL Recipients who have opened]**, available from the recipients list, displays a filter field that lets you select the delivery at which the filter is aimed.

  The **[!UICONTROL Preview]** button displays the result of the selected filter.

* The **[!UICONTROL Advanced parameters]** link lets you define additional settings. In particular, you can associate a SQL table with the filter to make it common to all editors that share the table.

  Select the **[!UICONTROL Do not restrict the filter]** option if you want to stop the user from overriding this filter.

  This option is enabled for "Recipients of a delivery" and "Recipients of deliveries belonging to a folder" filters offered in the delivery wizard that cannot be overloaded.

  ![](assets/s_ncs_user_filter_advanced_param.png)
