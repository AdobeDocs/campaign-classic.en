---
title: Updating the database structure
seo-title: Updating the database structure
description: Updating the database structure
seo-description: 
page-status-flag: never-activated
uuid: 7e249c34-8143-42a3-af36-6ada20612b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 0549d3bd-3d6c-4ba1-8ba9-094a4bf8ab8f
index: y
internal: n
snippet: y
---

# Updating the database structure{#updating-the-database-structure}

To apply the modifications made to the schemas, launch the database update wizard. This wizard is accessible via **Tools > Advanced > Update database structure**. It checks whether the physical structure of the database matches its logical description and executes the SQL update scripts.

![](assets/d_ncs_integration_schema_update.png)

The modules in the database are automatically populated and activated.

![](assets/d_ncs_integration_schema_update_select.png)

The **Add stored procedures** and **Import initialization data** options are used to launch the initial SQL scripts and the data packages executed when the database is created.

You can import a set of data from an external data package. To do this, select **Import a package** and enter the XML file of the package.

Follow the steps and view the database update SQL script:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>This is in an editing field and can be modified in order to delete or add SQL code.

Next, launch the database update:

![](assets/d_ncs_integration_schema_update3.png)

