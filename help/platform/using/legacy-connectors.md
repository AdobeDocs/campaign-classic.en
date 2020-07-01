---
title: Accessing an external database
seo-title: Accessing an external database
description: Accessing an external database
seo-description: 
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
---

# Legacy connectors {#legacy-connectors}

## Configure access to Hadoop 2.1 {#configure-access-to-hadoop}

### For Windows {#for-windows}

1. Install ODBC and [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) drivers for Windows.
1. Create the DSN (Data Source Name) by running the ODBC DataSource Adminstrator tool. A System DSN sample for Hive is provided for you to modify.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Create the Hadoop external account, as detailed in [this page](../../platform/using/external-accounts.md#hadoop-external-account) section.

### For Linux {#for-linux}

1. Install unixodbc for Linux.

   ```
   apt-get install unixodbc
   ```

1. Download and install ODBC drivers for Apache Hive from HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Check ODBC files location.

   ```

   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Create the DSN (Data Source Name) and edit the odbc.ini file. Then, create a DSN for your Hive connection.

   Here is an example for HDInsight to setup a connection called "viral":

   ```
   [ODBC Data Sources]
   vorac 

   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >The **UseNativeQuery** parameter here is very important. Campaign is Hive-aware and will not work correctly unless UseNativeQuery is set. Typically, the driver or Hive SQL Connector will rewrite queries and tamper the column ordering.

   The authentication setup depends on the Hive/Hadoop configuration. For instance, for HD Insight, use AuthMech=6 for user/password authentication, as described [here](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Export the variables.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Setup Hortonworks drivers via /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   You have to use UTF-16 to be able to connect with Campaign and unix-odbc (libodbcinst).

   ```
   [Driver]

   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp

   ODBCInstLib=libodbcinst.so
   ```

1. You can now test your connection using isql.

   ```
   isql vorac
   isql vorac -v
   ```

1. Create the Hadoop external account, as detailed in [this page](../../platform/using/external-accounts.md#hadoop-external-account) section.

## Configure access to Netezza {#configure-access-to-netezza}

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

1. In Campaign Classic, you can then configure your Netezza external account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

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

## Configure access to Sybase IQ {#configure-access-to-sybase-iq}

Connecting to a Sybase IQ external database in FDA requires additional configurations below on the Adobe Campaign server:

1. Make sure the unixodbc package is on the server.
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

1. In Campaign Classic, you can then configure your Sybase IQ external account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

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

## Configure access to Teradata {#configure-access-to-teradata}

Connecting to a Teradata external database in FDA requires certain additional configurations on the Adobe Campaign server. For more information on how to configure your Teradata database, refer to this [article](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html).

1. Install the [ODBC driver for Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   It is made up of three packages that can be installed on Red Hat (or CentOS)/Suse in the following order:

    * TeraGSS
    * tdicu1510 (install it using setup_wrapper.sh)
    * tdodbc1510 (install it using setup_wrapper.sh)

1. Configure the ODBC driver. The configuration can be carried out in the standard files: **/etc/odbc.ini** for general parameters and /etc/odbcinst.ini for declaring drivers:

    * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      "InstallDir" corresponds to the location of the **odbcinst.ini** file.

    * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed

      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Specify the environment variables of the Adobe Campaign server:

    * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 and /opt/teradata/client/15.10/odbc_64/lib.
    * **ODBCINI**: location of the odbc.ini file (for example /etc/odbc.ini).
    * **NLSPATH**: location of the opermsgs.cat file (/opt/teradata/client/15.10/msg/opermsgs.cat)

1. In Campaign Classic, you can then configure your Teradata external account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. To configure the **[!UICONTROL Teradata]** external account, you must specify:

     * **[!UICONTROL Type]**: Teradata

    * **[!UICONTROL Server]**: URL of the Teradata server

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password

    * **[!UICONTROL Database]**: Name of the database

## Configure access to SAP HANA {#configure-access-to-sap-hana}

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

1. In Campaign Classic, you can then configure your SAP Hana external account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. To configure the **[!UICONTROL SAP Hana]** external account, you must specify:

     * **[!UICONTROL Type]**: SAP Hana

    * **[!UICONTROL Server]**: URL of the SAP Hana server

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password
