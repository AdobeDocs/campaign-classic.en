---
solution: Campaign Classic
product: campaign
title: Creating a filter
description: Learn how to create a filter when performing queries
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
---
# Creating a filter {#creating-a-filter}

The filters available in Adobe Campaign are defined via filtering conditions which are created using the same operating mode as queries.

>[!NOTE]
>
>For more on creating filters, refer to [this section](../../platform/using/filtering-options.md).

The **[!UICONTROL Administration > Configuration > Predefined filters]** node contains all the filters used in the lists and overviews.

For example, the list of operators can be filtered by **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

The matching filter contains the query on the **[!UICONTROL Account disabled]** value of the **[!UICONTROL Operators]** schema:

![](assets/query_editor_filter_sample_2.png)

For the same list, the **[!UICONTROL By login or label]** filter lets you filter the data on the list based on the value entered in the filter field:

![](assets/query_editor_filter_sample_3.png)

It is built as follows:

![](assets/query_editor_filter_sample_4.png)

To match the filtering conditions, the operator account must check one of the following conditions:

* Its label contains the characters entered in the input field,
* The operator name contains the characters entered in the input field,
* The content of the description area contains the characters entered in the input field.

>[!NOTE]
>
>The **[!UICONTROL Upper]** function lets you deactivate the case-sensitive function.

The **[!UICONTROL Taken into account if]** column lets you define the application criteria for these filtering conditions. Here, the **$(/tmp/@text)** characters represent the content of the input field linked to the filter: 

![](assets/query_editor_filter_sample_5.png)

Here, **$(/tmp/@text)='agency'**

The **$(/tmp/@text)!=''** expression applies each condition when the input field isn't empty.
