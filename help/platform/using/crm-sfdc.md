---
product: campaign
title: Campaign - Salesforce CRM Connector
description: Learn how to connect Campaign and Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
TQID: https://experienceleague.adobe.com/LeUJ-F5dAECUrtkbvgwL0BN88Alofnh2rBWe7hIVGgI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences (Campaign)
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles (Campaign)
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences (Campaign)
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor (Campaign)
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management (Campaign)
---
# Connect Campaign and Salesforce.com{#connect-to-sfdc}


   
In this page, you will learn how to connect Campaign Classic to **Salesforce**.

Data synchronization is carried out via a dedicated workflow activity. [Learn more](../../platform/using/crm-data-sync.md).


The external account allows you to import and export Salesforce data into Adobe Campaign.
To configure CRM Connector for Salesforce, follow the steps below:

1. Create a new external account via the **[!UICONTROL Administration > Platform > External accounts]** node of the Adobe Campaign tree.
1. Select **[!UICONTROL Salesforce.com]**.
1. Enter settings to enable connection.

    ![](assets/ext_account_17.png)

    To configure the Salesforce CRM external account to work with Adobe Campaign, you need to provide the following details:

    * **[!UICONTROL Account]**
    Account used to sign in to Salesforce CRM.

    * **[!UICONTROL Password]**
    Password used to sign in to Salesforce CRM.

    * **[!UICONTROL Client identifier]**
    To know where to find your client identifier, refer to this [page](https://help.salesforce.com/articleView?id=000205876&type=1).

    * **[!UICONTROL Security token]**
    To know where to find your security token, refer to this [page](https://help.salesforce.com/articleView?id=000205876&type=1).

    * **[!UICONTROL API version]**
    Select the version of the API.
1. Run the configuration assistant to generate the available CRM table: the configuration assistant lets you collect tables and create the matching schema.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >To approve the setup, you need to log off and back on to the Adobe Campaign console.

1. Check the schema generated in Adobe Campaign in the **[!UICONTROL Administration > Configuration > Data schemas]** node.

   Example for **Salesforce** schema:

   ![](assets/crm_connectors_sfdc_table.png)

1. Once the schema is created, you can synchronize enumerations automatically from Salesforce to Adobe Campaign.

   To do this, click the **[!UICONTROL Synchronizing enumerations...]** link and select the Adobe Campaign enumeration that matches the Salesforce enumeration.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >You can replace all values of an Adobe Campaign enumeration with those of the CRM: to do this, select **[!UICONTROL Yes]** in the **[!UICONTROL Replace]** column.


   Click **[!UICONTROL Next]** and then **[!UICONTROL Start]** to start importing the list.

1. Check the imported values in the **[!UICONTROL Administration > Platform > Enumerations]** menu.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Multiple selection enumerations are not supported.

Campaign and Salesforce.com are now connected. You can set up data synchronization between the two systems. 

To synchronize data between Adobe Campaign data and SFDC, you need to create a workflow and use the **[!UICONTROL CRM connector]** activity.

![](assets/crm_connectors_sfdc_wf.png)

Learn more about data synchronization [in this page](../../platform/using/crm-data-sync.md).
