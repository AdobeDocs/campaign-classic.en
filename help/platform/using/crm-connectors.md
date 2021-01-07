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

1. To import CRM data or to export Adobe Campaign data to the CRM, you need to create a workflow and use the **[!UICONTROL CRM connector]** activity.

   ![](assets/crm_connectors_sfdc_wf.png)

Learn more about data synchronization [in this page](../../platform/using/crm-data-sync.md).

## Best practices and limitations

### Connect with Microsoft Dynamics

Learn how to connect Campaign and Microsoft Dynamics [in this section](../../platform/using/crm-ms-dynamics.md).

### Connect with Salesforce

You can connect your Salesforce CRM with Campaign and synchonize data between the two systems. Note that :

* Test production instances are supported.
* Assignation rules are supported.
* Multiple selection enumerations are not supported by Adobe Campaign.

### Connect with Oracle On Demand

You can connect your Oracle On Demand CRM with Campaign and synchonize data between the two systems. Note that :
* Adobe Campaign can synchronize any object available in the standard Oracle On Demand templates. If you have added personalized tables in Oracle On Demand, these won't be recovered in Adobe Campaign.
* API version v1.0 lets you sort or filter data during a query but does not let you do both simultaneously.
* The dates sent by Oracle On Demand do not contain time zone information.
* Multiple selection enumerations are not supported by Adobe Campaign.

To configure the **Oracle On Demand** connector to work with Adobe Campaign, follow the steps described in the [Implementation steps](#crm-implementation-steps) section.

Once configuration is done, you can synchronize data between the two systems through a workflow.

1. To import Oracle On Demand data into Adobe Campaign, create the following type of workflow:

   ![](assets/crm_connectors_ood_5.png)

   This workflow imports contacts via Oracle On Demand, synchronizes them with the existing Adobe Campaign data, deletes duplicate contacts, and updates the Adobe Campaign database.

   The **[!UICONTROL CRM Connector]** activity needs to be configured as shown here:

   ![](assets/crm_connectors_ood_6.png)

1. To export Adobe Campaign data to Oracle On Demand, create the following workflow:

   ![](assets/crm_connectors_ood_7.png)

   This workflow collects the relevant data using queries, then exports it into the Oracle On Demand contacts table.
