---
product: campaign
title: Configure access to Oracle
description: Learn how to configure access to Oracle in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
---
# Configure access to Oracle {#configure-access-to-oracle}

Use Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) option to process information stored in an external databases. Follow the steps below to configure access to Oracle.

1. Configure Oracle on [Linux](#oracle-linux) or [Windows](#azure-windows)
1. Configure the Oracle [external account](#oracle-external) in Campaign

## Oracle on Linux {#oracle-linux}

Connecting to an Oracle external database in FDA requires additional configurations below on the Adobe Campaign server.

1. Install the Oracle full client corresponding to your version of Oracle.
1. Add your TNS definitions to your installation. To do this, specify them in a **tnsnames.ora** file in the /etc/oracle repository. If this repository does not exist, create it.

   Then create a new TNS_ADMIN environment variable: export TNS_ADMIN=/etc/oracle and restart the machine.

1. Integrate Oracle into your Adobe Campaign server (nlserver). To do this, check that the **customer.sh** file is present in the "nl6" folder of the Adobe Campaign server tree structure and that it includes the links to the Oracle libraries.

   For example, for a client in 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >These values (particularly ORACLE_HOME), depends on your installation repositories. Make sure to check your tree structure before referencing these values.

1. Install the libraries necessary for Oracle:

    * **libclntsh.so**

      ```    
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

    * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. In Campaign Classic, you can then configure your [!DNL Oracle] external account. For more on how to configure your external account, refer to [this section](#oracle-external).

## Oracle on Windows {#oracle-windows}

Connecting to an Oracle external database in FDA requires additional configurations below on the Adobe Campaign server.

1. Install the Oracle client.

1. In the C:Oracle folder, create a **tnsnames.ora** file containing your TNS definition.

1. Add a TNS_ADMIN environment variable with C:Oracle as value and restart the machine.

1. In Campaign Classic, you can then configure your [!DNL Oracle] external account. For more on how to configure your external account, refer to [this section](#oracle-external).

## Oracle external account {#oracle-external}

The [!DNL Oracle] external account allows you to connect your Campaign instance to your Oracle external database.

1. From Campaign **[!UICONTROL Explorer]**, select **[!UICONTROL Administration]** '>' **[!UICONTROL Platform]** '>' **[!UICONTROL External accounts]**.

1. Choose **[!UICONTROL New]**.

1. Select **[!UICONTROL External database]** as your external account's **[!UICONTROL Type]**.

1. Configure the **[!UICONTROL Oracle]** external account, you must specify:

    * **[!UICONTROL Type]**: Oracle

    * **[!UICONTROL Server]**: Name of the DNS

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password

    * **[!UICONTROL Time zone]**: Server time zone

    ![](assets/oracle_config.png)
