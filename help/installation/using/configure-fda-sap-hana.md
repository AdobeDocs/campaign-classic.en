---
solution: Campaign Classic
product: campaign
title: Configure access to SAP HANA
description: Learn how to configure access to SAP HANA in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
---
# Configure access to SAP HANA {#configure-access-to-sap-hana}

Use Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) option to process information stored in an external databases. Follow the steps below to configure access to SAP HANA.

1. Configure [SAP HANA database](#sap-config)
1. Configure the SAP HANA [external account](#sap-external) in Campaign

## SAP HANA drivers {#sap-config}

Connecting to an SAP HANA external database in FDA requires certain additional configurations on the Adobe Campaign server:

1. Install the ODBC drivers for SAP HANA, according to the operating system that you use:

    * **hdb_client_linux.tgz** for Linux. Once unzipped, launch the hdbinst command and follow the instructions to finish installing the drivers.
    * **hdb_client_windows.zip** for Windows. Unzip the file and start the executable: **hdbinst.exe**. Follow the wizard instructions to finish installing the drivers.

1. Configure the ODBC driver. The configuration can be carried out in the standard files: /etc/odbc.ini for general parameters and /etc/odbcinst.ini for declaring drivers.

    * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/

      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      "InstallDir" corresponds to the location of the **odbcinst.ini** file.

    * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Specify the environment variables of the Adobe Campaign server:

    * **LD_LIBRARY_PATH**: It should include the link to your SAP Hana client (/usr/sap/hdbclient/libodbcHDB.so) by default).
    * **ODBCINI**: location of the odbc.ini file (for example /etc/odbc.ini).

## SAP HANA external account{#sap-external}

The SAP HANA external account allows you to connect your Campaign instance to your SAP HANA external database.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** '>' **[!UICONTROL Platform]** '>' **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. To configure the **[!UICONTROL SAP Hana]** external account, you must specify:

     * **[!UICONTROL Type]**: SAP Hana

    * **[!UICONTROL Server]**: URL of the SAP Hana server

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password
