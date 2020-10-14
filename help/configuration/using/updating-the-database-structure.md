---
title: Updating the database structure
seo-title: Updating the database structure
description: Updating the database structure
seo-description: 
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
---

# Updating the database structure{#updating-the-database-structure}

To apply the modifications made to the schemas, launch the database update wizard. This wizard is accessible via **[!UICONTROL Tools > Advanced > Update database structure]** . It checks whether the physical structure of the database matches its logical description and executes the SQL update scripts.

![](assets/d_ncs_integration_schema_update.png)

The modules in the database are automatically populated and activated.

![](assets/d_ncs_integration_schema_update_select.png)

The **[!UICONTROL Add stored procedures]** and **[!UICONTROL Import initialization data]** options are used to launch the initial SQL scripts and the data packages executed when the database is created.

You can import a set of data from an external data package. To do this, select **[!UICONTROL Import a package]** and enter the XML file of the package.

Follow the steps and view the database update SQL script:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>This is in an editing field and can be modified in order to delete or add SQL code.

Next, launch the database update:

![](assets/d_ncs_integration_schema_update3.png)

