---
product: campaign
title: Get Started with Federated Data Access
description: Learn how to access and process data in an external database
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
---
# Get Started with Federated Data Access {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

## Prerequisites {#operating-principle}

The FDA option allows you to extend your data model in a third-party database. It will automatically detect the structure of the targeted tables and use data from the SQL sources.

In order to use this capability, prerequisites are listed below:

* **Configuration**: the list of compatible external database depend on your [hosting model](../../installation/using/hosting-models.md).
* **External database version**: you need to have an external database that is compatible with the Adobe Campaign FDA module. 

    The list of database systems and compatible versions per hosting model is detailed in Campaign [Compatibility matrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA). 

* **Permissions**: users must also have the [necessary permissions](../../installation/using/remote-database-access-rights.md) in Adobe Campaign and on the external database.

