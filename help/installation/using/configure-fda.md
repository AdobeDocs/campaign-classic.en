---
solution: Campaign Classic
product: campaign
title: Configure FDA connectors
description: Learn configuration steps for FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
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

1. Install the drivers and set up the external account that correspond to your database on the Adobe Campaign server. Refer to the database-specific pages [listed below](#fda-specific-configuration)
1. Test the external account or create a temporary connection between Adobe Campaign and the external database. [Learn more](../../installation/using/connecting-to-database.md)
1. Create the schema of the external database in Adobe Campaign. This allows you to identify the data structure of the external database. [Learn more](../../installation/using/creating-data-schema.md)
1. If needed, create a new target mapping from the previously created schema. This is required if the recipients of your deliveries come from the external database. This implementation comes with limitations related to message personalization. [Learn more](../../installation/using/defining-data-mapping.md)

Once the data schema is created, data can be processed in Adobe Campaign workflows. For more on this, refer to [this section](../../workflow/using/accessing-an-external-database--fda-.md).

## Database specific configuration {#fda-specific-configuration}

Depending on the external databases that you want to be able to access from Adobe Campaign, you will need to carry out certain specific configurations. These configurations essentially involve installing drivers and declaring environment variables that belong to each RDBMS on the Adobe Campaign server, and configuring the external account.

Follow the links below to learn more:

* Connect Campaign and [Azure Synapse](../../installation/using/configure-fda-synapse.md)

* Connect Campaign and [Snowflake](../../installation/using/configure-fda-snowflake.md)

* Connect Campaign and [Hadoop](../../installation/using/configure-fda-hadoop.md)

* Connect Campaign and [Oracle](../../installation/using/configure-fda-oracle.md)

* Connect Campaign and [Netezza](../../installation/using/configure-fda-netezza.md)

* Connect Campaign and [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* Connect Campaign and [Teradata](../../installation/using/configure-fda-teradata.md)

* Connect Campaign and [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
