---
solution: Campaign Classic
product: campaign
title: Configure access to Netezza
description: Learn how to configure access to Netezza in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
---
# Configure access to Netezza {#configure-access-to-netezza}

Use Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) option to process information stored in an external databases. Follow the steps below to configure access to Netezza.

1. Install and configure [Netezza drivers](#netezza-config)
1. Configure the Netezza [external account](#netezza-external) in Campaign

## Netezza configuration {#netezza-config}

Connecting to a Netezza external database in FDA requires additional configurations below on the Adobe Campaign server:

1. Install the ODBC drivers for Netezza, according to the operating system that you use:

    * **nz-linuxclient-v7.2.0.0.tar.gz** for Linux. Select the folder that corresponds to your operating system (linux or linux64) and start the unpack command. You can leave the installation to be carried out in the repository that is suggested by default: "/usr/local/nz".
    * **nz-winclient-v7.2.0.0.zip** for Windows. Unzip the file and start the executable script that corresponds to your operating system: nzodbcsetup.exe or nzodbcsetup64.exe. Follow the wizard instructions to finish installing the drivers.

1. Configure the ODBC driver. The configuration can be carried out in the standard files: **/etc/odbc.ini** for general parameters and **/etc/odbcinst.ini** for declaring drivers.

    * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      "InstallDir" corresponds to the location of the odbcinst.ini file.

    * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed

      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Specify the environment variables of the Adobe Campaign server:

    * **LD_LIBRARY_PATH**: /usr/local/nz/lib and /usr/local/nz/lib64. "/usr/local/nz" corresponds to the installation repository offered by default when installing the drivers. Here you need to specify the repository that you have selected for the installation.
    * **ODBCINI**: location of the odbc.ini file (for example /etc/odbc.ini).
    * **NZ_ODBC_INI_PATH**: location of the odbc.ini file. Netezza also requires this second variable for using the odbc.ini file.

## Netezza external account {#netezza-external}

The Netezza external account allows you to connect your Campaign instance to your Netezza external database.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** '>' **[!UICONTROL Platform]** '>' **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. To configure the **[!UICONTROL Netezza]** external account, you must specify:

    * **[!UICONTROL Type]**: Netezza

    * **[!UICONTROL Server]**: URL of the Netezza server

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password

    * **[!UICONTROL Database]**: Name of the database

>[!NOTE]
>
>Operations on schemas containing automatically generated primary keys are not taken into account.  
>
>The table will be using the **Organize on** clause on the first index defined in the schema. As this clause is limited to 1 to 4 columns with Netezza, this index cannot contain more than 4 columns.
