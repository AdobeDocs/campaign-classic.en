---
solution: Campaign Classic
product: campaign
title: Creating a chart
description: Creating a chart
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: d32b614f-82c1-4363-816c-4ebedaa5cfe9
---
# Creating a chart{#creating-a-chart}

The data in the database can also be collected and displayed in a chart. Adobe Campaign provides a set of graphical representations. Their configuration is detailed below.

Charts are inserted directly into a report page via the right-click menu or the toolbar.

## Creation steps {#creation-steps}

To create a chart in a report, apply the following steps:

1. Edit the page where you want to display the chart and select the chart type on the toolbar.

   ![](assets/s_advuser_report_page_activity_04.png)

1. Enter a name and caption. If necessary, you can change the position of the caption using the drop-down list.

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. Click the **[!UICONTROL Data]** tab to define the data source and the series to be calculated.

   The statistics to be displayed in the chart can be calculated based on a query or on the context data, i.e. the data provided by the inbound transition of the current page (for more on this, refer to [Using context data](../../reporting/using/using-the-context.md#using-context-data)).

    * Click the **[!UICONTROL Filter data...]** link to define filtering criteria for the data in the database.
    
      ![](assets/reporting_graph_add_filter.png)

    * To used contextual data, select this option and click the **[!UICONTROL Advanced settings...]** link. Then select the data which the statistics will concern.
    
      ![](assets/reporting_graph_from_context.png)

      You will then be able to access the contextual data to define the values to be displayed in the chart:
    
      ![](assets/reporting_graph_select-from_context.png)

## Chart types and variants {#chart-types-and-variants}

Adobe Campaign offers various types of graphical representations. They are detailed below.

The chart type is selected when it is inserted into the page. 

![](assets/s_advuser_report_page_activity_04.png)

It can also be altered via the **[!UICONTROL Chart type]** section of the **[!UICONTROL General]** tab in the chart.

![](assets/reporting_change_graph_type.png)

Variants depend on the selected chart type. They are selected via the **[!UICONTROL Variants...]** link.

### Breakdown: pie charts {#breakdown--pie-charts}

This type of graphical representation lets you display an overview of the measured elements.

Pie charts only enable you to analyze one variable.

![](assets/reporting_graph_type_sector_1.png)

The **[!UICONTROL Variants]** link lets you personalize the overall rendering of the chart.

![](assets/reporting_graph_type_sector_2.png)

Pie charts let you enter the value of the inner radius in the appropriate field.

For example:

0.00 traces a full circle.

![](assets/s_ncs_advuser_report_sector_exple1.png)

0.40 traces a circle with a radius of 40%.

![](assets/s_ncs_advuser_report_sector_exple2.png)

1.00 only traces the outside of the circle.

![](assets/s_ncs_advuser_report_sector_exple3.png)

### Evolution: curves and areas {#evolution--curves-and-areas}

This type of graphical representation lets you understand the evolution of one or more measures in time. 

![](assets/reporting_graph_type_curve.png)

### Comparison: histograms {#comparison--histograms}

Histograms enable you to compare the values of one or more variables.

For these types of charts, the following options are offered in the **[!UICONTROL Variants]** window:

![](assets/reporting_select_graph_var.png)

Check the **[!UICONTROL Display caption]** option to show the caption with the chart and choose its position:

![](assets/reporting_select_graph_legend.png)

When appropriate, you can stack values together.

![](assets/reporting_graph_type_histo.png)

If necessary, you can reverse the value display sequence. To do this, select the **[!UICONTROL Reverse stacking]** option.

### Conversion: funnel {#conversion--funnel}

This type of chart lets you track the conversation rate of measured elements.

### Progress: gauge {#progress--gauge}

This type of chart lets you display the progress of a value compared to a defined objective. In the example below, the black dial shows the number of deliveries successfully sent (76) out of a goal of 100 deliveries. The gauge is divided into three ranges that correspond to specific statuses.

![](assets/reporting_graph_type_gauge.png)

These elements are defined when configuring the chart.

![](assets/reporting_graph_type_gauge1.png)

* The **[!UICONTROL Value]** field is represented by a black dial in the chart. It represents the element whose progress you would like to calculate. The value to be represented must have already been saved to be used.
* The **[!UICONTROL Goal]** field represents the maximum value to achieve.
* Using the **[!UICONTROL Other mark]** field you can add a second indicator to the chart.
* The **[!UICONTROL Display range]** fields let you specify the values between which the report is calculated.
* The **[!UICONTROL Value ranges]** field lets you attribute statuses (None, Bad, Acceptable, Good) to a set of values to better illustrate the progress.

In the **[!UICONTROL Display settings]** section, the **[!UICONTROL Change appearance...]** lets you configure the way the chart is displayed.

![](assets/reporting_graph_type_gauge2.png)

The **[!UICONTROL Display the value below the gauge]** option lets you display the value progress below the chart.

The **[!UICONTROL Aperture ratio]** field, which must be between 0 and 1, lets you edit the report's aperture in a more or less complete circle. In the example above, the value 0.50 corresponds to a semi-circle.

The **[!UICONTROL Width]** field lets you edit the chart size.

## Interaction with the chart {#interaction-with-the-chart}

You can define an action when the user clicks the chart. Open the **[!UICONTROL Interaction events]** window and select the action you want to perform.

Possible interaction types and their configurations are detailed in [this section](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/s_ncs_advuser_report_wizard_017.png)

## Calculating statistics {#calculating-statistics}

Charts let you display statistics on the collected data.

These statistics are defined via the **[!UICONTROL Series parameters]** section of the **[!UICONTROL Data]** tab.

To create a new statistic, click the **[!UICONTROL Add]** icon and configure the appropriate window. The available calculation types are detailed below.

![](assets/reporting_add_statistics.png)

For more on this, refer to [this section](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).
