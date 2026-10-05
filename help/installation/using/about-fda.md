---
product: campaign
title: Get Started with Federated Data Access
description: Learn how to access and process data in an external database
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: 'https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
---
# Get Started with Federated Data Access {#about-federated-data-access}



Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

## Prerequisites {#operating-principle}

The FDA option allows you to extend your data model in a third-party database. It will automatically detect the structure of the targeted tables and use data from the SQL sources.

In order to use this capability, prerequisites are listed below:

* **Configuration**: the list of compatible external database depend on your [hosting model](../../installation/using/hosting-models.md).
* **External database version**: you need to have an external database that is compatible with the Adobe Campaign FDA module. 

    The list of database systems and compatible versions per hosting model is detailed in Campaign [Compatibility matrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA). 

* **Permissions**: users must also have the [necessary permissions](../../installation/using/remote-database-access-rights.md) in Adobe Campaign and on the external database.

