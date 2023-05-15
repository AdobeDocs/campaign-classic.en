---
product: campaign
title: About cubes
description: Get started with cubes
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
hide: yes
hidefromtoc: yes
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
---
# Get started with cubes{#about-cubes}

 

## Terminology {#terminology}

Specific terms when working with cubes are listed below.

* **Cube** - A cube is a representation of multidimensional information: it provides end users with structures designed for interactive data analysis.

* **Fact table/schema** - The facts table (or fact schema) contains the raw or elementary data on which analyses will be based. These are mainly large volume tables (possibly with linked tables) with potentially long calculations. For example, a fact table can be: the broadlog table, the purchase table, etc.

* **Dimension** - Dimensions let you segment data into groups: once they have been created, the dimensions serve as analysis axes. In most cases, for a given dimension, several levels will be defined. For example, for a temporal dimension, the levels will be months, days, hours, minutes, etc. This set of levels represents the dimension hierarchy and enables various levels of data analysis.

* **Binning** - For some fields, you can define binning to group values and make it easier to read information. Binning is applied to levels. We recommend that you define binning when there is a possibility of many different values.

* **Measure** - The most frequent measures are sum, average, maximum, minimum, standard deviation etc. Measures can be calculated: for instance, the acceptance rate of an offer is the ratio of the number of times it was presented compared to the number of times it was accepted.

## Cube workspace {#cube-workspace}

Cubes are stored in the **[!UICONTROL Administration > Configuration > Cubes]** node.

![](assets/s_advuser_cube_node.png)

The main contexts of use for cubes are as follows:

* Data exports can be carried out directly in a report, designed in the **[!UICONTROL Reports]** tab of the Adobe Campaign platform.

  To do this, create a new report and select the cube you want to use.

  ![](assets/cube_create_new.png)

  Cubes appear like templates based on which reports are created. Once you have chosen a template, click **[!UICONTROL Create]** to configure and view the matching report.

  You can adapt measures, change the display mode or configure the table, then display the report using the main button.

  ![](assets/cube_display_new.png)

* You can also reference a cube in the **[!UICONTROL Query]** box of a report to use its indicators, as shown below:

  ![](assets/s_advuser_query_using_a_cube.png)

* You can also insert a pivot table based on a cube into any page of a report. To do this, reference the cube to be used in the **[!UICONTROL Data]** tab of the pivot table on the concerned page.

  ![](assets/s_advuser_cube_in_report.png)

  For more on this, refer to [Explore the data in a report](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
