---
product: campaign
title: Creating the data schema for FDA
description: Learn how to create the data schema for FDA
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
TQID: https://experienceleague.adobe.com/eC7jDm92g943ymcfEQjaeevS7qzIJWJR0zCtnP2Ny7o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
---
# Creating the data schema {#creating-the-data-schema}



To create a schema on an external database:

1. Click the **[!UICONTROL New]** button above the list of data schemas and choose **[!UICONTROL Access external data]**.

    ![](assets/wf_new_schema_fda.png)

1. Enter a **[!UICONTROL Namespace]** and  **[!UICONTROL Name]** for the schema and select the **[!UICONTROL External account]** which will enable connection to the database. This enables access to the list of tables available in the external base.

    ![](assets/wf_new_schema_select_table_fda.png)

1. From the **[!UICONTROL Table name]** field, choose the table which contains the data to be collected. 

    With Snowflake, you can select here your views if the database user has been granted the correct privileges. Note that when using views, Adobe Campaign will not be able to automatically generate the XML schema, you will have to create it yourself. For more information on views, refer to [Snowflake documentation](https://docs.snowflake.com/en/user-guide/views-introduction.html).

    ![](assets/wf_new_schema_select_table_fda.png)

1. Click **[!UICONTROL OK]** to confirm. Adobe Campaign automatically detects the structure of the selected table and generates the logical schema. Please note that Adobe Campaign does not generate links.

1. Click **[!UICONTROL Save]** to confirm creation.

    >[!CAUTION]
    >
    >With Snowflake, a primary key is mandatory.

    ![](assets/wf_new_schema_generate_fda.png)

The indexes are created automatically when mapping a table (standard or FDA mapping).
