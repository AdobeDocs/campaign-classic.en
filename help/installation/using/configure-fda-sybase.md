---
product: campaign
title: Configure access to Sybase IQ
description: Learn how to configure access to Sybase IQ in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
---
# Configure access to Sybase IQ {#configure-access-to-sybase-iq}

![](../../assets/v7-only.svg)

Use Campaign **Federated Data Access** (FDA) option to process information stored in an external databases. Follow the steps below to configure access to Sybase IQ.

1. Configure [Sybase IQ database](#configuring-sybase) 
1. Configure the Sybase IQ [external account](#sybase-external) in Campaign

## Sybase IQ configuration {#configuring-sybase}

Connecting to a Sybase IQ external database in FDA requires additional configurations below on the Adobe Campaign server.

>[!NOTE]
>
>Before starting, make sure the **unixodbc** package is on the server.

1. Install **iq_odbc**. An error can occur at the end of the installation. This error can be ignored.

1. Install **iq_client_common**. A Java error can occur at the end of the installation. This error can be ignored.

1. Configure the ODBC driver. The configuration can be carried out in the standard files: /etc/odbc.ini for general parameters and /etc/odbcinst.ini for declaring drivers:

    * **/etc/odbc.ini** (replace values like `<server_alias>` characters by your own):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so

      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

    * **/etc/odbcinst.ini**

      ```

      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Add the path for the new libodbc16.so library in the LD_LIBRARY_PATH variable. To do that:

    * If you are using a customer.sh file to declare your path: add the path /opt/sybase/IQ-16_0/lib64 for the LD_LIBRARY_PATH variable.
    * Otherwise, use a Unix command.

## Sybase IQ external account {#sybase-external}

The Sybase IQ external account allows you to connect your Campaign instance to your Sybase IQ external database.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** '>' **[!UICONTROL Platform]** '>' **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. To configure the **[!UICONTROL Sybase IQ]** external account, you must specify:

     * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

    * **[!UICONTROL Server]**: Corresponds to the ODBC connection (`<server_alias>`) defined in step 5. Not necessarily the name of the server itself.

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password

    * **[!UICONTROL Database]**: Name of the database

>[!NOTE]
>
>For Windows, you must install the Sybase IQ client on the Adobe Campaign server and create an ODBC connection. Make sure you create a system data source when the Adobe Campaign server (nlserver) is running as a service in Windows.
