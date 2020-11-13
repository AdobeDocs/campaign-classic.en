---
title: Configure FDA connectors
description: Learn configuration steps for FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
---

# Configuring FDA connectors {#specific-configurations-by-database-type}

Depending on the external databases that you want to be able to access from Adobe Campaign, you will need to carry out certain specific configurations. These configurations essentially involve installing drivers and declaring environment variables that belong to each RDBMS on the Adobe Campaign server.

As a general rule, you need to install the corresponding client layer on the external database on the Adobe Campaign server.

>[!NOTE]
>
>Compatible versions are listed in [Campaign Compatibility Matrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
>

## Configuration steps {#fda-configuration-steps}

To set up access to an external database with FDA, configuration steps are:

1. Install the drivers that correspond to your database on the Adobe Campaign server. Drivers are listed in the database-specific pages [listed below](#fda-specific-configuration). 
1. [Create and configure an external account](../../platform/using/connecting-to-database.md) that allows you to establish the connection between Adobe Campaign and the external database. For more information on external accounts in Campaign, refer to [this page](../../platform/using/external-accounts.md).
1. [Create the schema](../../platform/using/creating-data-schema.md) of the external database in Adobe Campaign. This allows you to recognize the data structure of the external database.
1. If needed, [create a new target mapping](../../platform/using/defining-data-mapping.md) from the previously created schema. This is required if the recipients of your deliveries come from the external database. This implementation comes with limitations related to message personalization.

Once the data schema is created, data can be processed in Adobe Campaign workflows. For more on this, refer to [this section](../../workflow/using/accessing-an-external-database--fda-.md).

## Database specific configuration {#fda-specific-configuration}

Depending on the external databases that you want to be able to access from Adobe Campaign, you will need to carry out certain specific configurations. These configurations essentially involve installing drivers and declaring environment variables that belong to each RDBMS on the Adobe Campaign server.

Follow the links below to learn more:

* [Azure Synapse](../../platform/using/configure-fda-synapse.md)

* [Snowflake](../../platform/using/configure-fda-snowflake.md)

* [Hadoop](../../platform/using/configure-fda-hadoop.md)

* [Oracle](../../platform/using/configure-fda-oracle.md)

* [Netezza](../../platform/using/configure-fda-netezza.md)

* [Sybase IQ](../../platform/using/configure-fda-sybase.md)

* [Teradata](../../platform/using/configure-fda-teradata.md)

* [SAP HANA](../../platform/using/configure-fda-sap-hana.md)
