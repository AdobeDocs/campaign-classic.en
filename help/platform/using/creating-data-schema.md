---
title: Accessing an external database
seo-title: Accessing an external database
description: Accessing an external database
seo-description: 
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
---

# Creating the data schema {#creating-the-data-schema}

To create a schema on an external database:

1. Click the **[!UICONTROL New]** button above the list of data schemas and choose **[!UICONTROL Access external data]**.

    ![](assets/wf_new_schema_fda.png)

1. Enter a name and a description for the schema and select the external account which will enable connection to the database. This enables access to the list of tables available in the external base. Choose the table which contains the data to be collected.

    ![](assets/wf_new_schema_select_table_fda.png)

1. Click **[!UICONTROL OK]** to confirm. Adobe Campaign automatically detects the structure of the selected table and generates the logical schema. Please note that Adobe Campaign does not generate links.

1. Click **[!UICONTROL Save]** to confirm creation.

    >[!CAUTION]
    >
    >With Snowflake, a primary key is mandatory.

    ![](assets/wf_new_schema_generate_fda.png)

The indexes are created automatically when mapping a table (standard or FDA mapping).
