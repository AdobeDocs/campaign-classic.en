---
solution: Campaign Classic
product: campaign
title: CRM Connectors
description: CRM Connectors
audience: platform
content-type: reference
topic-tags: connectors
---

# CRM Connectors{#crm-connectors}

## Get started with CRM connectors {#about-crm-connectors}

Adobe Campaign provides various CRM connectors for linking your Adobe Campaign platform to your third-party systems. These CRM connectors enable you to synchronize contacts, accounts, purchases, etc. They make for easy integration of your application with various third-party and business applications.

These connectors enable quick and easy data integration: Adobe Campaign provides a dedicated wizard for collecting and selecting from the tables available in the CRM. This guarantees two-directional synchronization to make sure data is up-to-date at all times throughout the systems.

>[!NOTE]
>
>This feature is available in Adobe Campaign through the **CRM connectors** dedicated package.


### Compatible systems {#compatible-crm-systems-and-limitations}

Supported CRM and versions are detailed in Campaign [Compatibility matrix](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>The CRM connectors only work with a secure URL (https).

### Implementation steps {#crm-implementation-steps}

Learn how to connect Campaign and Microsoft Dynamics [in this section](../../platform/using/crm-ms-dynamics.md)

In general, to use CRM connectors in Adobe Campaign, apply the following steps:

1. Create a new external account via the **[!UICONTROL Administration > Platform > External accounts]** node of the Adobe Campaign tree.
1. Run the configuration wizard to generate the available CRM tables : the configuration wizard lets you collect tables and create the matching schema.
 Click **[!UICONTROL Start]** to run the execution.

   Example for Salesforce configuration wizard:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >To approve the setup, you need to log off and back on to the Adobe Campaign console.

1. Check the schema generated in Adobe Campaign in the **[!UICONTROL Administration > Configuration > Data schemas]** node.

   Example for Salesforce schema:

   ![](assets/crm_connectors_sfdc_table.png)

1. Once the schema is created, you can synchronize enumerations automatically via the CRM to Adobe Campaign.

   To do this, click the **[!UICONTROL Synchronizing enumerations...]** link and select the Adobe Campaign enumeration that matches the CRM enumeration.

   You can replace all values of an Adobe Campaign enumeration with those of the CRM: to do this, select **[!UICONTROL Yes]** in the **[!UICONTROL Replace]** column.

   Example for Salesforce enumerations:

   ![](assets/crm_connectors_sfdc_enum.png)

   Click **[!UICONTROL Next]** and then **[!UICONTROL Start]** to start importing the list.

1. Check the imported values in the **[!UICONTROL Administration > Platform > Enumerations]** menu.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Multiple selection enumerations in Salesforce are not supported.

1. To import CRM data or to export Adobe Campaign data to the CRM, you need to create a workflow and use the **[!UICONTROL CRM connector]** activity.

   ![](assets/crm_connectors_sfdc_wf.png)

Learn more about data synchronization [in this page](../../platform/using/crm-data-sync.md).

