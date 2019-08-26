---
title: Installing the client console
seo-title: Installing the client console
description: Installing the client console
seo-description: 
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
---

# Installing the client console{#installing-the-client-console}

The Adobe Campaign console installation procedure is detailed below.

Before you install the Adobe Campaign console, check the prerequisites listed in the [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

To install the Adobe Campaign console, apply the following steps:

1. Open a Web browser and download the console from the following address:

   [https://`<your adobe="" campaign="" server=""> : <port number="">  /nl/jsp/logon.jsp </port></your>`](https://machine/nl/jsp/logon.jsp).

1. In the identification window, enter your login and password. 

   ![](assets/s_ncs_install_setup_download01.png)

   If necessary, use the credentials of the internal account defined during instance creation.

1. Click the **[!UICONTROL Download]** link on the installation page.
1. Download and save the client setup file.
1. Execute the downloaded file on a computer on Windows: The installation starts up. The default installation path of the client console is **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, where 'X' is '6' or '7', according to your Adobe Campaign version.
1. Once the installation program has finished, start the console from the Windows **[!UICONTROL Start]** menu (in the **Adobe Campaign** program group).

>[!NOTE]
>
>On Windows, you can launch the **nlclient.exe** file directly from the **[INSTALL]/bin** directory on a Windows server, where **[INSTALL]** is the access path for the Adobe Campaign installation folder.  
>To create a new connection, refer to [Creating an instance and logging on](https://helpx.adobe.com/campaign/standard/installation/using/creating-an-instance-and-logging-on.html).

