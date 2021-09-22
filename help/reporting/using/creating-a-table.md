---
product: campaign
title: Creating a table
description: Creating a table
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 05f76bdf-6dcd-4360-9e72-0ba6a4dd0d5e
---
# Creating a table{#creating-a-table}

![](../../assets/common.svg)

You can add a table to a report to display data. This can be a pivot table created based on cube measurements, a list with group, or a table containing a breakdown of values. 

![](assets/s_advuser_report_page_activity_05.png)

## Creating a list with group {#creating-a-list-with-group}

A **[!UICONTROL List with group]** type table lets you group data in the table and produce statistics on it. For instance, you can create totals and sub-totals for the data. Each group has its own header, detail and footer line.

>[!CAUTION]
>
>The **[!UICONTROL Page]** activity containing the table must be preceded by a **[!UICONTROL Query]** or **[!UICONTROL Script]** activity to collect the data to be analyzed in the report. For more on these activities, refer to [Collecting data to analyze](../../reporting/using/collecting-data-to-analyze.md) and [Script activity](../../reporting/using/advanced-functionalities.md#script-activity).

### Operating principle {#operating-principle}

It may happen that you need to analyze several data categories at once. A list with group lets you combine data and create statistics on various groups of data within the same table. To do this, you can create a group in the table.

In the following example, the group shows all the campaigns in the database, the deliveries, and the number of messages sent per delivery and per campaign.

It lets you list the campaigns (**[!UICONTROL Label (Campaign)]**, the list of deliveries (**[!UICONTROL Label]** ) linked to the campaign, and lets you count the number of messages sent per delivery (**[!UICONTROL Processed)]**, before adding them up for each campaign (**[!UICONTROL Sum(@processed)]** ). 

![](assets/s_advuser_ergo_listgroup_005.png)

### Implementation steps {#implementation-steps}

A full implementation example is provided here: [Use case: Create a report with a group list](#use-case--create-a-report-with-a-group-list).

Please note the following steps to create a 'List with group' type table:

1. Go to the report chart and place a **[!UICONTROL Query]** activity. Refer to [Collecting data to analyze](../../reporting/using/collecting-data-to-analyze.md). 
1. Fill in the source table and select the fields of the table which the statistics will concern. 
1. Place a **[!UICONTROL Page]** activity in the chart. For more on this, refer to [Static elements](../../reporting/using/creating-a-new-report.md#static-elements). 
1. Insert a **[!UICONTROL List with group]** type table into the page. 
1. Specify the data path, or the table selected as a data source in the query.

   This step is mandatory if you want to recover the fields in the source table later and insert them into the cells of the table.

1. Creating the table and its content.
1. Display the finalized report in the **[!UICONTROL Preview]** tab. You can then publish the report and export it into a different format if necessary. For more on this, refer to [Exporting a report](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Adding lines and columns {#adding-lines-and-columns}

By default, a **[!UICONTROL List with group]** type table includes a header, a detail line, and a footer line.

The group itself includes header, detail and footer lines.

* **Header line**: this line lets you give a title to the columns of the table.

  ![](assets/s_advuser_ergo_listgroup_003a.png)

* **Detail line**: this line contains statistical values.

  ![](assets/s_advuser_ergo_listgroup_004.png)

* **Footer line**: this line lets you display the total values.

  ![](assets/s_advuser_ergo_listgroup_003.png)

Lines and columns can be added to suit your needs.

The group can be placed on any line of the table and includes its own header, detail and footer lines. 

![](assets/s_advuser_ergo_listgroup_019.png)

**Line and column**: to add or delete a line or a column, go to an existing line or column and use the right-click menu.

![](assets/s_advuser_ergo_listgroup_006.png)

The nature of the line you add depends on the location of the cursor. For example, to add a header line, place your cursors on a header, then click **[!UICONTROL Add > A line above/below]**.

![](assets/s_advuser_ergo_listgroup_006a.png)

The width of the columns can be modified via the **[!UICONTROL Column format]** item.

**Group**: to add a group, go to a line and select the matching item in the drop-down menu.

![](assets/s_advuser_ergo_listgroup_007.png)

### Defining cell content {#defining-cell-content}

To edit a cell of the table and define its content and format, go to the cell and use the right-click menu.

Use the **[!UICONTROL Expression]** menu entry to select the values to display.

![](assets/s_advuser_ergo_listgroup_010.png)

* To insert the values to be analyzed directly into the table, select them among the available fields.

  The list of available fields coincides with the content of the query before the table in the report construction chart.

  ![](assets/s_advuser_ergo_listgroup_011.png)

* Enter a label for a cell, the header one for example.

  To do this, use the same process as for inserting a field into the database, but don't select an expression. Enter the label in the **[!UICONTROL Label]** field. It will be displayed as is.

* Calculating an aggregate (an average, a sum, etc.) and displaying it in the cell.

  To do this, use the **[!UICONTROL Aggregates]** menu entry and select the desired campaign.

  ![](assets/s_advuser_ergo_listgroup_008.png)

### Defining cell format {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

To define the cell format, the **[!UICONTROL Cell format...]** menu lets you access all formatting options available for the selected cell.

These options enable you to personalize the final rendering of the report and make it easier to read information.

Use the **[!UICONTROL Carriage return]** field when exporting data to Excel: select the **[!UICONTROL Yes]** value to force the carriage return. This value will be kept when exporting. For more on this, refer to [Exporting a report](../../reporting/using/actions-on-reports.md#exporting-a-report).

The **[!UICONTROL Cell format]** window lets you access the following tab:

* The **[!UICONTROL Value]** tab
* The **[!UICONTROL Borders]** tab
* The **[!UICONTROL Click]** tab
* The **[!UICONTROL Extra]** tab

The **[!UICONTROL Value]** tab lets you change the font and the various value attributes or to define a format based on their nature. 

![](assets/s_advuser_ergo_listgroup_009.png)

The format changes data display: for example, the **[!UICONTROL Number]**, **[!UICONTROL Monetary]** and **[!UICONTROL Percentage]** formats allow you to align the figures on the right and display decimal points.

Example of how to configure a currency format: you can specify the currency which the values are expressed in, choose whether or not to separate thousands, and show negative values in red. The position of the currency symbol depends on the language of the operator defined in their profile.

![](assets/s_advuser_ergo_listgroup_012.png)

Configuration example for dates: you can choose whether or not to display the time.

![](assets/s_advuser_ergo_listgroup_013.png)

The **Borders** tab lets you add borders to the lines and columns in the table. Adding borders to the cells may lead to performance issues when exporting large reports into Excel.

![](assets/s_advuser_ergo_listgroup_014.png)

If necessary, you can define borders in the table template (**[!UICONTROL Administration > Configuration > Form rendering]** ).

In this case, you'll have the following syntax:

In the Web tab:

```
 .tabular td {
 border: solid 1px #000000;
 }
```

In the Excel tab:

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

The **[!UICONTROL Click]** tab lets you define an action when the user clicks the content of a cell or of the table.

In the example below, clicking the value in the cell lets you display the second page of the report: it will contain information on the delivery in the cell.

![](assets/s_advuser_ergo_listgroup_015.png)

The **Extra** tab lets you link a visual to your data, such as a colored mark or a value bar. The colored mark is used when the table is shown as a legend in a chart. For more on this, refer to the implementation example: [Step 5 - Create the second page](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Use case: Create a report with a group list {#use-case--create-a-report-with-a-group-list}

In this example, we are going to create a two-page report: the first page will contain the list and the total deliveries per campaign, as well as the number of messages sent. Delivery names will be clickable links and will enable you to go on to the second page of the report to view the breakdown of deliveries per email domain for the selected delivery with a table and a chart. On the second page, the table will serve as a legend for the chart.

![](assets/reporting_quick_start_report-final.png)

### Step 1 - Create a report {#step-1---create-a-report}

Create a new report that concerns the campaign schema, **[!UICONTROL Campaigns (nms)]**.

![](assets/s_advuser_report_listgroup_001.png)

Click **[!UICONTROL Save]** to create the report.

Go to the chart and add the first components to be used for designing the report content: a first query and a first page.

![](assets/reporting_quick_start_diagram.png)

### Step 2 - Create the first query {#step-2---create-the-first-query}

The first query lets you collect deliveries linked to each campaign. The goal is to display a report on the various deliveries of the Adobe Campaign database linked to each campaign.

Double-click the first query to edit it, then apply the following steps to configure it:

1. Start by changing the schema on which the query's source is applied: select the **[!UICONTROL Deliveries (nms)]** schema.
1. Click the **[!UICONTROL Edit query]** link and display the advanced fields.

   ![](assets/reporting_quick_start_query-1.png)

1. Select the following fields:

    * the delivery label,
    * the primary key of the delivery,
    * the campaign label,
    * the indicator of processed deliveries,
    * the foreign key of the Campaign link,
    * the error rate indicator.

   ![](assets/s_advuser_report_listgroup_002.png)

   Link an alias to each field: this is recommended to facilitate the selection of data from the table that will be added to the first page of the report.

   For this example, we'll use the following aliases:

    * Label: **@label**
    * Primary key: **@deliveryId**
    * Label (Campaign): **@label1**
    * Processed: **@processed**
    * Foreign key of the 'Campaign' ('id' field) link: **@operationId**
    * Error rate: **@errorRatio**

1. Click the **[!UICONTROL Next]** button twice to get to the **[!UICONTROL Data filtering]** step.

   Add a filtering condition to collect only the deliveries linked to a campaign.

   The syntax of this filter is as follows: "Foreign key of the 'Campaigns' link greater than 0". 

   ![](assets/reporting_quick_start_query_filter.png)

1. Click **[!UICONTROL Finish]** to save these conditions, then click **[!UICONTROL Ok]** to close the query editor.

### Step 3: Create the first page {#step-3--create-the-first-page}

In this step, we are going to configure the first page of the report. To configure it, apply the following steps:

1. Open the **[!UICONTROL Page]** activity and enter its title, for instance **Deliveries** in this case.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Insert a list with group via the toolbar and enter its label, for instance: List of deliveries per campaign.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Click the **[!UICONTROL Table data XPath...]** link and select the delivery link, i.e. `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. Click the **[!UICONTROL Data]** tab and change layout of the table: add three columns on the right.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Add a group.

   ![](assets/s_advuser_report_listgroup_008.png)

   This group will enable you to group campaigns and the deliveries linked to them.

1. In the group window, reference the **Foreign key of the 'Campaign' link** and close the window.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Edit the first cell of the group header and insert the **[!UICONTROL Label]** field of the campaigns as an expression.

   ![](assets/s_advuser_report_listgroup_009.png)

1. Edit the second cell of the details line and select the deliveries **[!UICONTROL Label]**.

   ![](assets/s_advuser_report_listgroup_011.png)

1. Edit the format of this cell and open the **[!UICONTROL Click]** tab. Configure the adequate options so that when the users clicks the name of a delivery, it opens in the same window. 

   ![](assets/s_advuser_report_listgroup_0111.png)

   To do this, select a **[!UICONTROL Next page]** type action and select **[!UICONTROL In the same window]** as an open option.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. In the lower section of the window, click **[!UICONTROL Add]** and specify the **`/vars/selectedDelivery`** path and the **[!UICONTROL @deliveryId]** expression that matches the alias of the primary key of the delivery, as defined in the query created previously. This formula lets you access the selected delivery.

   ![](assets/s_advuser_report_listgroup_010.png)

1. Edit the second cell of the footer line of the group and enter **[!UICONTROL Total per campaign]** as a label.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Edit the third cell of the header line of the group and enter **[!UICONTROL Number of messages sent]** as a label.

   ![](assets/s_advuser_report_listgroup_013.png)

   This information coincides with the column title.

1. Edit the third cell of the detail line and select the processed message indicator as an expression.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Edit the third cell of the footer line of the group, select the processed delivery indicator and apply the **[!UICONTROL Sum]** aggregate to it.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Edit the fourth cell of the detail line and select the **error delivery error rate** as an expression.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Select this cell to display a value bar representing the delivery error rate.

   To do this, access the cell format, then go to the **[!UICONTROL More]** tab. Select the **[!UICONTROL Value bar]** entry in the drop-down list and select the **[!UICONTROL Hide the cell value]** option.

   ![](assets/s_advuser_report_listgroup_023.png)

   You may now view a rendering of the report. Click the **[!UICONTROL Preview]** tab and select the **[!UICONTROL Global]** option: this shows the list of all deliveries in the Adobe Campaign database that are linked to a campaign.

   ![](assets/s_advuser_report_listgroup_025.png)

   We recommend using the **[!UICONTROL Preview]** tab to make sure the data in your table is properly selected and configured. Once this is done, you can go on to formatting your table.

1. Apply the **[!UICONTROL Bold]** style to the cells that show the total per campaign and the total number of messages processed.

   ![](assets/s_advuser_report_listgroup_024.png)

1. Click the 1st cell of the group header line, the one that displays the campaign name, and select **[!UICONTROL Edit > Merge to right]**.

   ![](assets/s_advuser_report_listgroup_026.png)

   Merging the first two cells of the group header line will re-align the campaign title and the list of deliveries linked to it.

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >We recommend waiting until your report is built before merging cells since merging is irreversible.

### Step 4 - Create the second query {#step-4---create-the-second-query}

We want to add a second query and a second page to display the detail of a delivery when the user of the report clicks on it. Before adding the query, edit the page you have created and enable the outgoing transition so that it can be linked to the query.

1. Add a new query after the **[!UICONTROL Page]** activity and edit its schema: select the **[!UICONTROL Recipient delivery logs]** schema.

   ![](assets/reporting_quick_start_query-2.png)

1. Edit the query and define the output columns. To display the number of deliveries per email domain, you need to:

    * calculate the sum of primary keys to count the number of delivery logs:
    
      ![](assets/reporting_quick_start_query-2_count.png)

    * collect recipient email domains and group information on this field: to do this, select the **[!UICONTROL Group]** option in the domain name column.

   ![](assets/reporting_quick_start_query-2_filter.png)

   Link the following aliases to the fields:

    * count(primary key): **@count**
    * Email domain (Recipient): **@domain**
    
      ![](assets/reporting_quick_start_query-2_alias.png)

1. Click the **[!UICONTROL Next]** button twice: this takes you to the **[!UICONTROL Data filtering]** step.

   Add a filtering condition to collect only the information linked to the selected delivery.

   The syntax is as follows: Foreign key of the 'Delivery' link equals the value of the setting `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Close the query configuration window and add a page to the chart, just after the second query.

### Step 5 - Create the second page {#step-5---create-the-second-page}

1. Edit the page and enter its label: **Email domains**.
1. Uncheck the **[!UICONTROL Enable output transitions]** option: this is the last page of the report and will not be followed by another activity.

   ![](assets/s_advuser_report_listgroup_028.png)

1. Add a new list with a group using the right-click menu and call it **Email domains per recipient**.
1. Click the **[!UICONTROL Table data XPath...]** and select the **[!UICONTROL Recipient delivery logs]** link.

   ![](assets/s_advuser_report_listgroup_029.png)

1. In the **[!UICONTROL Data]** tab, adapt the table as follows:

    * Add two columns on the right hand side.
    * In the first cell of the detail line, add the **[!UICONTROL rowNum()-1]** expression to count the number of lines. Then alter the format of the cell: in the **[!UICONTROL Extra]** tab, select **[!UICONTROL Color tab]** and click **[!UICONTROL Ok]**.
    
      ![](assets/s_advuser_report_listgroup_018.png)

      This configuration will enable you to use the table as a caption for the chart.
    
    * In the second cell of the detail line, add the **[!UICONTROL Email domain(Recipient)]** expression.
    * In the third cell of the detail line, add the **[!UICONTROL count(primary key)]** expression.

   ![](assets/s_advuser_report_listgroup_019.png)

1. Add a pie chart to the page using the right-click menu and assign the **Email domains** label to it. For more information, refer to [Chart types and variants](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Click the **[!UICONTROL Variants]** link and deselect the **[!UICONTROL Display label]** and the **[!UICONTROL Display caption]** options. 
1. Check that no value sorting is configured. For more on this, refer to [this section](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report).

   ![](assets/s_advuser_report_listgroup_0191.png)

1. In the **[!UICONTROL Data]** tab, change the data source: select **[!UICONTROL Context data]** from the drop-down list.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Then click **[!UICONTROL Advanced settings]** and select the link to the recipient delivery logs.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. In the **[!UICONTROL Chart type]** section, select the **[!UICONTROL Email domain]** variable.
1. Then add the calculation to be carried out: select the sum as an operator.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Click the **[!UICONTROL Detail]** button to select the field which the count will concern, then close the configuration window.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Save the report.

   Your page is now configured.

### Step 6 - Viewing the report {#step-6---viewing-the-report}

To view the result of this configuration, click the **[!UICONTROL Preview]** tab and select the **[!UICONTROL Global]** option.

The first page of your report details the list of all deliveries included in the database.

![](assets/s_advuser_report_listgroup_021.png)

If you click the link of one of these deliveries, it shows the chart showing the breakdown of email domains for this delivery. You are now on the second page of the report and can return to the previous page by clicking the appropriate button.

![](assets/s_advuser_report_listgroup_022.png)

## Creating a breakdown or pivot table {#creating-a-breakdown-or-pivot-table}

This type of table lets you display statistics calculated on the data in the database.

The configuration of these types of reports is similar to the one used for the descriptive analysis wizard. For more on this, refer to [this page](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template).

For more on creating a pivot table, refer to [this section](../../reporting/using/using-cubes-to-explore-data.md).
