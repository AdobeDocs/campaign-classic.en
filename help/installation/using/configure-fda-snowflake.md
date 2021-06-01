---
product: campaign
title: Configure access to Snowflake
description: Learn how to configure access to Snowflake in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
---
# Configure access to Snowflake {#configure-access-to-snowflake}

Use Campaign **Federated Data Access** (FDA) option to process information stored in an external database. Follow the steps below to configure access to [!DNL Snowflake].

1. Configure [!DNL Snowflake] on [CentOS](#snowflake-centos), [Windows](#snowflake-windows) or [Debian](#snowflake-debian)
1. Configure the [!DNL Snowflake] [external account](#snowflake-external) in Campaign


>[!NOTE]
>
>[!DNL Snowflake] connector is available for hosted and on-premise deployments. For more on this, refer to [this page](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake on CentOS {#snowflake-centos}

To configure [!DNL Snowflake] on CentOS, follow the steps below:

1. Download the ODBC drivers for [!DNL Snowflake]. [Click here](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) to start downloading.
1. You then need to install the ODBC drivers on CentOs with the following command:

    ```
    rpm -Uvh unixodbc
    rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
    ```

1. After downloading and installing the ODBC drivers, you need to restart Campaign Classic. To do so, run the following command:

    ```
    /etc/init.d/nlserver6 stop
    /etc/init.d/nlserver6 start
    ```

1. In Campaign, you can then configure your [!DNL Snowflake] external account. For more on how to configure your external account, refer to [this section](#snowflake-external).

## Snowflake on Windows {#snowflake-windows}

1. Download the [ODBC driver for Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Note that you need administrator-level privileges to install the driver. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure the ODBC driver. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign, you can then configure your [!DNL Snowflake] external account. For more on how to configure your external account, refer to [this section](#snowflake-external).

## Snowflake on Debian {#snowflake-debian}

1. Download the ODBC drivers for [!DNL Snowflake]. [Click here](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) start downloading.

1. You then need to install the ODBC drivers on Debian with the following command:

     ```
     apt-get install unixodbc
     apt-get install snowflake-odbc-x.xx.x.x86_64.deb
     ```

1. After downloading and installing the ODBC drivers, you need to restart Campaign Classic. To do so, run the following command:

     ```
     systemctl stop nlserver.service
     systemctl start nlserver.service
     ```

1. In Campaign, you can then configure your [!DNL Snowflake] external account. For more on how to configure your external account, refer to [this section](#snowflake-external).

## Snowflake external account {#snowflake-external}

You need to create a [!DNL Snowflake] external account to connect your Campaign instance to your [!DNL Snowflake] external database.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** '>' **[!UICONTROL Platform]** '>' **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]**.

1. Select **[!UICONTROL External database]** as your external account's **[!UICONTROL Type]**.

1. Configure the **[!UICONTROL Snowflake]** external account, you must specify:

    * **[!UICONTROL Type]**: [!DNL Snowflake]

    * **[!UICONTROL Server]**: URL of the [!DNL Snowflake] server

    * **[!UICONTROL Account]**: Name of the user

    * **[!UICONTROL Password]**: User account password

    * **[!UICONTROL Database]**: Name of the database

    ![](assets/snowflake.png)

1. Click the **[!UICONTROL Parameters]** tab then the **[!UICONTROL Deploy functions]** button to create functions.

    ![](assets/snowflake_2.png)

The connector supports the following options:

| Option   |  Description |
|---|---|
|  workschema | Database schema to use for work tables |
|  warehouse | Name of the default warehouse to use. It will override the user's default. |
|  TimeZoneName |  By default empty, which means that the system time zone of the Campaign Classic app server is used. The option can be used to force the TIMEZONE session parameter. <br>For more on this, refer to [this page](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
|  WeekStart |  WEEK_START session parameter. By default set to 0. <br>For more on this, refer to [this page](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
|  UseCachedResult | USE_CACHED_RESULTS session parameter. By default set to TRUE. This option can be used to disable Snowflake cached results. <br>For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
