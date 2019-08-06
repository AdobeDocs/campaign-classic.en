---
title: Extraction (file)
seo-title: Extraction (file)
description: Extraction (file)
seo-description: 
page-status-flag: never-activated
uuid: a8c194ae-cad8-4709-9d42-020c23d9235c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 126bc399-6b7f-4e62-929b-50061e1cbdd7
index: y
internal: n
snippet: y
---

# Extraction (file){#extraction-file}

You can extract data from a workflow table in an external file using the **Extraction (file)** activity.

>[!CAUTION]
>
>This activity must always have an inbound transition which contains the data to be extracted.

To configure data extraction, apply the following steps:

1. Specify the name of the output file: this name can contain variables, inserted via the personalization button to the right of the field.
1. Click **Edit the file format...** to select the data to be extracted.

   ![](assets/s_advuser_extract_file_param.png)

   The **Handle groupings (GROUP BY + HAVING)** option adds an extra step to filter the final result of the aggregate, for example on a given purchase order type, customers who have ordered more than 10 times, etc.

1. If necessary, you can add new columns to the output file, such as computing or processing results for example. To do this, click the **Add** icon 

   ![](assets/s_advuser_extract_file_add_col.png)

   In the additional line, click the **Edit expression** icon to define the content of the new column. 

   ![](assets/s_advuser_extract_file_add_exp.png)

   You will then access the selection window. Click **Advanced selection** to choose the process to be applied to the data.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Choose the desired formula from the list.

   ![](assets/s_advuser_extract_file_agregate_values.png)

## List of aggregate functions {#list-of-aggregate-functions}

The following is a list of available aggregate functions:

* **Count** to count all non-null values of the field to be aggregated, including duplicate values (of the aggregated field),

  **Distinct** to count the total number of different and non-null values of the field to aggregate (duplicate values are excluded before the calculation),

* **Sum** to calculate the sum of values of a numerical field,
* **Minimum value** to calculate the minimum values of a field (numerical or otherwise),
* **Maximum value** to calculate the maximum values of a field (numerical or otherwise),
* **Average** to calculate the average of the values of a numerical field.

