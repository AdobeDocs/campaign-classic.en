---
solution: Campaign Classic
product: campaign
title: Creating a shared connection
description: Creating a shared connection
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
---
# Creating a shared connection{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* Schema extensions made on the schemas used by [Message Center technical workflows](../../message-center/using/technical-workflows.md) on either control or execution instances need to be duplicated on the other instances used by Adobe Campaign transactional messaging module.
>* The control instance and the execution instance(s) must be installed on different machines. They cannot share the same Campaign instance.
>

## Control instance {#control-instance}

If you have a broken-down architecture, you need to specify the execution instances linked to the control instance and connect them. Transactional message templates are deployed to the execution instances. The connection between the control instance and the execution instances is created by configuring the **[!UICONTROL Execution instance]** type external accounts. You need to create as many external accounts as there are execution instances.

>[!NOTE]
>
>When execution instances are used by several control instances, data can be divided by folder and by operator. For more on this, refer to [Using several control instances](#using-several-control-instances).

To create an execution instance type external account, apply the following steps:

1. Go to the **[!UICONTROL Administration > Platform > External accounts]** folder.
1. Select one of the execution instance type external accounts provided out-of-the-box with Adobe Campaign, right-click and choose **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Change the label according to your needs. 

   ![](assets/messagecenter_create_extaccount_002.png)

1. Select the **[!UICONTROL Enabled]** option to make the external account operational.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Specify the address of the server on which the execution instance is installed.

   ![](assets/messagecenter_create_extaccount_004.png)

1. The account must match the Message Center Agent as defined in the operator folder. By default, the out-of-the-box account provided by Adobe Campaign is **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Enter the password of the account as defined in the operator folder.

   >[!NOTE]
   >
   >To avoid entering a password each time you log on to the instance, you can specify the IP address of the control instance in the execution instance. For more on this, refer to [Execution instance](#execution-instance).

1. Specify the recovery method to be used by the execution instance.

   The data to recover is forwarded to the control instance by the execution instance, to add to transactional message and event archives.

   ![](assets/messagecenter_create_extaccount_007.png)

   Data collection occurs either via a Web service which uses HTTP/HTTPS access, or via the Federated Data Access (FDA) module.

   >[!NOTE]
   >
   >Please note that when using FDA over HTTP, only execution instances using a PostgreSQL database are supported. MSSQL or Oracle databases are not supported.

   The second method is recommended if the control instance has direct access to the database of the execution instances. If not, choose the Web service access. The FDA account to specify coincides with the connection to the databases of the various execution instances created on the control instance.

   ![](assets/messagecenter_create_extaccount_008.png)

   For more information on Federated Data Access (FDA), refer to [Accessing an external database](../../installation/using/about-fda.md).

1. Click **[!UICONTROL Test the connection]** to make sure the control instance and the execution instance are linked up.

   ![](assets/messagecenter_create_extaccount_006.png)

1. Each execution instance must be associated with an identifier. This identifier can be attributed on each execution instance either manually, by using the deployment wizard (refer to [Identifying execution instances](../../message-center/using/identifying-execution-instances.md)), or automatically, by clicking the **Initialize connection** button from the control instance.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## Execution instance {#execution-instance}

In order for the control instance to be able to connect to the execution instance without having to give a password, simply enter the IP address of the control instance in the **Message Center** access rights section. However, empty passwords are forbidden by default.

To use an empty password, go to the execution instances and define a security zone limited to the IP address of the information system that delivers the events. This security zone must allow empty passwords and accept `<identifier> / <password>` type connections. For more on this, refer to [this section](../../installation/using/security-zones.md).

>[!NOTE]
>
>When execution instances are used by several control instances, data can be divided by folder and by operator. For more on this, refer to [Using several control instances](#using-several-control-instances).

1. Go to the operator folder in the execution instance ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Select the **Message Center** agent.

   ![](assets/messagecenter_operator_001.png)

1. Select the **[!UICONTROL Edit]** tab, click **[!UICONTROL Access rights]** , and then click the **[!UICONTROL Edit the access parameters...]** link.

   ![](assets/messagecenter_operator_002.png)

1. In the **[!UICONTROL Access settings]** window, click the **[!UICONTROL Add a trusted IP mask]** link and add the IP address of the control instance.

   ![](assets/messagecenter_operator_003.png)

## Using several control instances {#using-several-control-instances}

You can share an execution cluster with various control instances. This type of architecture requires the following configuration.

For example if your company manages two brands, each with its own control instance: **Control 1** and **Control 2**. Two execution instances are also used. You need to enter a different Message Center operator for each control instance: an **mc1** operator for the **Control 1** instance and an **mc2** operator for the **Control 2** instance.

In the tree of all the execution instances, create one folder per operator (**Folder 1** and **Folder 2**), and restrict each operator's data access to their folder.

### Configuring control instances {#configuring-control-instances}

1. In the **Control 1** control instance, create one external account per execution instance, and enter the **mc1** operator in each external account. The **mc1** operator will thereafter be created on all the execution instances (refer to [Configuring execution instances](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. In the **Control 2** control instance, create one external account per execution instance, and enter the **mc2** operator in each external account. The **mc2** operator will thereafter be created on all the execution instances (refer to [Configuring execution instances](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >For more on configuring a control instance, refer to [Control instance](#control-instance).

### Configuring execution instances {#configuring-execution-instances}

In order to use several control instances, this configuration has to be performed on ALL execution instances.

1. Create one folder per operator in the **[!UICONTROL Administration > Production > Message Center]** node: **Folder 1** and **Folder 2**. For more on creating folders and views, refer to [this page](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. Create the **mc1** and **mc2** operators by duplicating the Message Center operator provided by default (**mc**). For more on creating operators, refer to [this section](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** and **mc2** operators must have **[!UICONTROL Message Center execution]** rights and they cannot have access to the Adobe Campaign client console. An operator must always be linked with a security zone. For more on this, refer to [this section](../../installation/using/security-zones.md).

1. For each operator, check the **[!UICONTROL Restrict to information found in sub-folders of]** box, and select the relevant folder (**Folder 1** for the **mc1** operator and **Folder 2** for the **mc2** operator).

   ![](assets/messagecenter_multi_control_5.png)

1. Give each operator read and write permissions for their folder. To do this, right-click the folder and select **[!UICONTROL Properties]** . Then select the **[!UICONTROL Security]** tab and add the relevant operator (**mc1** for **Folder 1** and **mc2** for **Folder 2**). Make sure that the **[!UICONTROL Read/Write data]** boxes are checked.

   ![](assets/messagecenter_multi_control_6.png)
