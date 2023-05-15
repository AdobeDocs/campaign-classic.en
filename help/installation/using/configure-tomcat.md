---
product: campaign
title: Campaign Tomcat configuration
description: Campaign Tomcat configuration
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-on-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
---
# Configure Apache Tomcat {#configuring-tomcat}



Adobe Campaign uses an **embedded web servlet called Apache Tomcat** to process HTTP/HTTPS requests between the application and any external interface (including Client Console, tracked URL links, SOAP calls, and others). There is often an external web server (usually IIS or Apache) in front of this for any external-facing Adobe Campaign instances.

Learn more about Tomcat in Campaign and how to locate your Tomcat version in [this page](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>This procedure is restricted to **on-premise** deployments. 
>

## Default port for Apache Tomcat {#default-port-for-tomcat}

When the 8080 listening port of the Tomcat server is already busy with another application required for your configuration, you need to replace the 8080 port with a free one (8090 for instance). To change it, edit the **server.xml** file saved in the **/tomcat-8/conf** directory of the Adobe Campaign installation folder.

Then modify the port of the JSP relay pages. To do this, change the **serverConf.xml** file saved in the **/conf** directory of the Adobe Campaign installation directory.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...

```

## Map a folder in Apache Tomcat {#mapping-a-folder-in-tomcat}

To define customer specific settings, you can create a **user_contexts.xml** file in the **/tomcat-8/conf** folder, which also contains the **contexts.xml** file.

This file will contain the following type of information:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

If necessary, this operation can be reproduced on the server-side.

## Hide the Tomcat error report {#hide-tomcat-error-report}

For security reasons, we strongly recommend that you hide the Tomcat error report. Here are the steps.

1. Open the **server.xml** file located in the **/tomcat-8/conf** directory of the Adobe Campaign installation folder:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Add the following element at the bottom after all existing context elements:

    ```
    <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
    ```
    
1. Restart the nlserver and Apache web servers.
