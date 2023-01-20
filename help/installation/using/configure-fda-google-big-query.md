---
product: campaign
title: Configure access to Google BigQuery
description: Learn how to configure access to Google BigQuery in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
---
# Configure access to Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Use Adobe Campaign Classic **Federated Data Access** (FDA) option to process information stored in an external database. Follow the steps below to configure access to [!DNL Google BigQuery].

1. Configure [!DNL Google BigQuery] on [Windows](#google-windows) or [Linux](#google-linux)
1. Configure the [!DNL Google BigQuery] [external account](#google-external) in Adobe Campaign Classic
1. Set up [!DNL Google BigQuery] connector bulk load on [Windows](#bulk-load-windows) or [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] connector is available for hosted, hybrid and on-premise deployments. For more on this, refer to [this page](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery on Windows {#google-windows}

### Driver set up on Windows {#driver-window}

1. Download the [ODBC driver for Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configure the ODBC driver in Windows. For more on this, refer to [this page](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. For the [!DNL Google BigQuery] connector to work, Adobe Campaign Classic requires the following parameters to connect:

    * **[!UICONTROL Project]**: create or use an existing project. 
    
        For more information, refer to this [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

    * **[!UICONTROL Service account]**: create a service account.

        For more information, refer to this [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

    * **[!UICONTROL Key File Path]**: the **[!UICONTROL Service account]** requires a **[!UICONTROL Key File]** for a [!DNL Google BigQuery] connection through ODBC. 
    
        For more information, refer to this [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

    * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** is optional for an ODBC connection. Since every query needs to provide the dataset where the table is located, specifying a **[!UICONTROL Dataset]** is mandatory for [!DNL Google BigQuery] FDA Connector in Adobe Campaign Classic. 
    
        For more information, refer to this [page](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic, you can then configure your [!DNL Google BigQuery] external account. For more on how to configure your external account, refer to [this section](#google-external).

### Bulk load set up on Windows {#bulk-load-window}

>[!NOTE]
>
>You need Python installed for Google Cloud SDK to work. 
>
>We recommend using Python3, see this [page](https://www.python.org/downloads/).

Bulk Load utility allows faster transfer, which is achieved through Google Cloud SDK.

1. Download Windows 64-bit (x86_64) archive from this [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) and extract it in the corresponding directory.

1. Run the `google-cloud-sdk\install.sh` script. You need to accept the setting of path variable. 

1. After the installation, check that the path variable `...\google-cloud-sdk\bin` is set. If not, add it manually.

1. In the  `..\google-cloud-sdk\bin\bq.cmd` file, add the `CLOUDSDK_PYTHON` local variable, which will redirect to the location of the Python installation. 
    
    For example:

    ![](assets/google-big-query_1.png)

1. Restart Adobe Campaign Classic for the changes to be taken into account.

## Google BigQuery on Linux {#google-linux}

### Driver set up on Linux {#driver-linux}

Before setting up the driver, note that script and commands must be ran by root user. It is also recommended to use Google DNS 8.8.8.8, while running the script.

To configure [!DNL Google BigQuery] on Linux, follow the steps below:

1. Before the ODBC installation, check that the following packages are installed on your Linux distribution: 

    * For Red Hat/CentOS:

        ```
        yum update
        yum upgrade
        yum install -y grep sed tar wget perl curl
        ```

    * For Debian:

        ```
        apt-get update
        apt-get upgrade
        apt-get install -y grep sed tar wget perl curl
        ```

1. Update system before installation:

    * For Red Hat/CentOS:

        ```
        # install unixODBC driver manager
        yum install -y unixODBC
        ```

    * For Debian:

        ```
        # install unixODBC driver manager
        apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
        ```

1. Before running the script, you can obtain more info by specifying --help argument:

    ```
    cd /usr/local/neolane/nl6/bin/fda-setup-scripts
    ./bigquery_odbc-setup.sh --help
    ```
    
1. Access the directory where the script is located and run the following script as root user:

    ```
    cd /usr/local/neolane/nl6/bin/fda-setup-scripts
    ./bigquery_odbc-setup.sh
    ```

### Bulk load set up on Linux {#bulk-load-linux}

>[!NOTE]
>
>You need Python installed for Google Cloud SDK to work. 
>
>We recommend using Python3, see this [page](https://www.python.org/downloads/).

Bulk Load utility allows faster transfer, which is achieved through Google Cloud SDK.

1. Before the ODBC installation, check that the following packages are installed on your Linux distribution: 

    * For Red Hat/CentOS:

        ```
        yum update
        yum upgrade
        yum install -y python3
        ```

    * For Debian:

        ```
        apt-get update
        apt-get upgrade
        apt-get install -y python3
        ```

1. Access the directory where the script is located and run the following script:

    ```
    cd /usr/local/neolane/nl6/bin/fda-setup-scripts
    ./bigquery_sdk-setup.sh
    ```

## Google BigQuery external account {#google-external}

You need to create a [!DNL Google BigQuery] external account to connect your Adobe Campaign Classic instance to your [!DNL Google BigQuery] external database.

1. From Adobe Campaign Classic **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** '>' **[!UICONTROL Platform]** '>' **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]**.

1. Select **[!UICONTROL External database]** as your external account's **[!UICONTROL Type]**.

1. Configure the [!DNL Google BigQuery] external account, you must specify:

    * **[!UICONTROL Type]**: [!DNL Google BigQuery]

    * **[!UICONTROL Service account]**: Email of your **[!UICONTROL Service account]**. For more information on this, refer to [Google Cloud documentation](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

    * **[!UICONTROL Project]**: Name of your **[!UICONTROL Project]**. For more information on this, refer to [Google Cloud documentation](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

    * **[!UICONTROL Key file Path]**: 
        * **[!UICONTROL Upload key file to the server]**: select **[!UICONTROL Click here to upload]** if you choose to upload the key through Adobe Campaign Classic.
        
        * **[!UICONTROL Enter manually the key file path]**: copy/paste your absolute path in this the field if you choose to use a pre-existing key.

    * **[!UICONTROL Dataset]**: Name of your **[!UICONTROL Dataset]**. For more information on this, refer to [Google Cloud documentation](https://cloud.google.com/bigquery/docs/datasets-intro).

    ![](assets/google-big-query.png)

The connector supports the following options:

| Option   |  Description |
|:-:|:-:|
|  ProxyType | Type of proxy used to connect to BigQuery through ODBC and SDK connectors. </br>HTTP (default), http_no_tunnel, socks4 and socks5 are currently supported. |
|  ProxyHost | Hostname or IP address where the proxy can be reached. |
| ProxyPort | Port number the proxy is running on, e.g. 8080 |
| ProxyUid | Username used for the authenticated proxy |
| ProxyPwd | ProxyUid password |
| bqpath | Note that this is applicable for bulk-load tool only (Cloud SDK). </br> To avoid using PATH variable or if the google-cloud-sdk directory has to be moved to another location, you can specify with this option the exact path to the cloud sdk bin directory on the server. |
