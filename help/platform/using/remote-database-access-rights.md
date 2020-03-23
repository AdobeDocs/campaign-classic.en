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

# Remote database access rights {#remote-database-access-rights}

First, so that the user can carry out operations on an external database via FDA, the latter must have a specific named right in Adobe Campaign.

1. Select the **[!UICONTROL Administration > Access Management > Named Rights]** node in the Adobe Campaign explorer.
1. Create a new right by specifying your chosen label.
1. The **[!UICONTROL Name]** field must take the following format **user:base@server**, where :

    * **user** corresponds with the name of the user in the external database.
    * **base** corresponds with the name of the external database.
    * **server** corresponds with the name of the external database server.

      >[!NOTE]
      >
      >The **:base** part is optional in Oracle.

1. Save the named right then link it to your chosen user from the **[!UICONTROL Administration > Access Management > Operators]** node of the Adobe Campaign explorer.

Then, to process the data contained in an external database, the Adobe Campaign user must have at least 'Write' rights on the database to be able to create worktables. These are deleted automatically by Adobe Campaign.

Generally speaking, the following rights are necessary:

* **CONNECT**: connection to the remote database,
* **READ Data**: read-only access to tables containing customer data,
* **READ 'MetaData'**: access to the server data catalogs to obtain the table structure,
* **LOAD**: mass loading in work tables (required when working on collections and joins),
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** (recommended): for monitoring performances in case of problems,
* **WRITE Data** (depending on the integration scenario).

>[!NOTE]
>
>The database administrator needs to make these rights match with the rights specific to each database engine. For more information, refer to [RDBMS specific rights](https://docs.adobe.com/content/help/en/campaign-classic/using/assets/fda_rdbms_rights.pdf).