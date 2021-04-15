---
solution: Campaign Classic
product: campaign
title: Configure access to Vertica
description: Learn how to configure access to Vertica in FDA
audience: platform
content-type: reference
topic-tags: connectors
---

# Configure access to Vertica {#configure-fda-vertica}

Use Campaign **Federated Data Access** (FDA) option to process information stored in an external database. Follow the steps below to configure access to [!DNL Vertica].

1. Configure [!DNL Vertica] on [CentOS](#vertica-centos), [Windows](#vertica-windows) or [Debian](#vertica-debian)
1. Configure the [!DNL Vertica] [external account](#vertica-external) in Campaign


>[!NOTE]
>
>[!DNL Vertica] connector is available for hybrid and on-premise deployments. For more on this, refer to [this page](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica on CentOS {#vertica-centos}

To configure [!DNL Vertica] on CentOS, follow the steps below:

1. Download the ODBC drivers for [!DNL Vertica]. [Click here](https://www.vertica.com/download/vertica/client-drivers/) and download the latest Linux RPM.

1. You then need to install unixODBC with the following command:

    ```
    yum search unixODBC
    yum install unixODBC.x86_64
    ```

1. If you have previously installed the [!DNL Vertica] Server, an ODBC driver will already be installed. In this case, update the drive as follows:

    ```
    #Switch to root
    sudo su
 
    #Install the package (add --force to update it)
    rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
 
    #Open odbcinst.ini
    vi /etc/odbcinst.ini
 
    #Add a section for Vertica and save
    [Vertica]
    Description = Vertica ODBC Driver
    Driver = /opt/vertica/lib64/libverticaodbc.so
 
    #Open odbc.ini
    vi /etc/odbc.ini
 
    #Add your DSN in ODBC Data Sources section, for example:
    [ODBC Data Sources]
    VMart = "VMart database on Vertica"
 
    #Add a DSN definition section below, for example:
    [VMart]
    Description = Vmart Database
    Driver = Vertica
    Database = VMart
    Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
    UID = dbadmin
    PWD = <password>
    Port = 5433
    
    #Cleanup
    #Remove the ODBC package
    rm vertica-client-x.x.x-x.x86_64.rpm
    ```

1. In Adobe Campaign, you can then configure your [!DNL Vertica] external account. For more on how to configure your external account, refer to [this section](#vertica-external).

## Vertica on Windows {#vertica-windows}

1. Download the [ODBC driver for Windows](https://www.vertica.com/download/vertica/client-drivers/). To install the driver for Windows, you will need to enable .NET Framework 3.5 or the installation wizard will try to automatically enable and download it.

1. Configure the ODBC driver in Windows. For more on this, refer to [this page](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign, you can then configure your [!DNL Vertica] external account. For more on how to configure your external account, refer to [this section](#vertical-external).

## Vertica on Debian {#vertica-debian}

1. Download the ODBC drivers for [!DNL Vertica]. [Click here](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) start downloading.

1. You then need to install unixODBC with the following command:

    ```
    apt-get install unixODBC
    ```

1. If you have previously installed the [!DNL Vertica] Server, an ODBC driver will already be installed. In this case, update the drive as follows:

    ```
    #Switch to root
    sudo su
 
    #Move or copy the downloaded file and change to /root
    mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
    cd /
 
    #Uncompress the file you downloaded
    tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
 
    #Remove the tar.gz since it is not needed anymore
    rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
 
    #Open odbcinst.ini
    vi /etc/odbcinst.ini
 
    #Add a section for Vertica and save
    [Vertica]
    Description = Vertica ODBC Driver
    Driver = /opt/vertica/lib64/libverticaodbc.so
 
    #Open odbc.ini
    vi /etc/odbc.ini
 
    #Add your DSN in ODBC Data Sources section, for example:
    [ODBC Data Sources]
    VMart = "VMart database on Vertica"
 
    #Add a DSN definition section below, for example:
    [VMart]
    Description = Vmart Database
    Driver = Vertica
    Database = VMart
    Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
    UID = dbadmin
    PWD = <password>
    Port = 5433
    ```

1. In Adobe Campaign, you can then configure your [!DNL Vertica] external account. For more on how to configure your external account, refer to [this section](#vertica-external).

## Vertica external account {#vertica-external}

You need to create a [!DNL Vertica] external account to connect your Campaign instance to your [!DNL Vertica] external database.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** '>' **[!UICONTROL Platform]** '>' **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]**.

1. Select **[!UICONTROL External database]** as your external account's **[!UICONTROL Type]**.

1. Configure the **[!UICONTROL Vertica]** external account, you must specify:

    * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

    * **[!UICONTROL Server]**: URL of the [!DNL Vertica] server

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password

    * **[!UICONTROL Database]**: Name of the database

    ![](assets/vertica.png)
