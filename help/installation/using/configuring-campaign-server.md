---
solution: Campaign Classic
product: campaign
title: Configuring Campaign server
description: Configuring Campaign server
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
---
# Configuring Campaign server{#configuring-campaign-server}

The section below details server-side configurations that can be performed to match your needs and your environment specificities.

These configurations must be performed by administrators and for **On-premise** hosting models only.

For **Hosted** deployments, server-side settings can be configured by Adobe only. However, some settings can be set up within the Control Panel (for example, IP allowlist management or URL permissions).

>[!NOTE]
>
>Control Panel is accessible to all Admin users. The steps to grant Admin access to a user are detailed in [this section](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
>
>Note that your instance must be hosted on AWS and upgraded with the latest [Gold Standard](../../rn/using/gs-overview.md) build or the [latest GA build (21.1)](../../rn/using/latest-release.md). Learn how to check your version in [this section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). To check if your instance is hosted on AWS, follow the steps detailed in [this page](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

For more information, refer to these sections:

* [Control Panel documentation](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)
* [Hosting models](../../installation/using/hosting-models.md)
* [Campaign Classic On-premise & Hosted capability matrix](../../installation/using/capability-matrix.md)
* [Hybrid and hosted models configuration steps](../../installation/using/hosting-models.md)

Campaign Classic configuration files are stored in the **conf** folder of the Adobe Campaign installation folder. The configuration is spread over two files:

* **serverConf.xml**: general configuration for all instances. This file combines the technical parameters of the Adobe Campaign server: these are shared by all instances. The description of some of these parameters is detailed below. The different nodes and parameters and listed in this [section](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (where **instance** is the name of the instance): specific configuration of the instance. If you share your server among several instances, please enter the parameters specific to each instance in their relevant file.

## Configuring Tomcat {#configuring-tomcat}

### Default port for Tomcat {#default-port-for-tomcat}

When the 8080 listening port of the Tomcat server is already busy with another application required for your configuration, you need to replace the 8080 port with a free one (8090 for instance). To change it, edit the **server.xml** file saved in the **/tomcat-8/conf** directory of the Adobe Campaign installation folder.

Then modify the port of the JSP relay pages. To do this, change the **serverConf.xml** file saved in the **/conf** directory of the Adobe Campaign installation directory. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...

```

### Mapping a folder in Tomcat {#mapping-a-folder-in-tomcat}

To define customer specific settings, you can create a **user_contexts.xml** file in the **/tomcat-8/conf** folder, which also contains the **contexts.xml** file.

This file will contain the following type of information:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

If necessary, this operation can be reproduced on the server-side.

## Personalizing delivery parameters {#personalizing-delivery-parameters}

The delivery parameters are defined in the **serverConf.xml** configuration file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

General server configuration and commands are detailed in [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

You can also carry out the following configurations depending on your needs and settings.

### SMTP relay {#smtp-relay}

The MTA module acts as a native mail transfer agent for SMTP broadcast (port 25).

It is, however, possible to replace it by a relay server if your security policy requires it. In that case, the global throughput will be the relay one (provided that the relay server throughput is inferior to the Adobe Campaign one).

In this case, these parameters are set by configuring the SMTP server in the **`<relay>`** section. You must specify the IP address (or host) of the SMTP server used to transfer mail and its associated port (25 by default).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>This operating mode implies serious limitations on deliveries, as it can greatly reduce the throughput because of the relay server intrinsic performances (latency, bandwith...). Moreover, the capacity to qualify synchronous delivery errors (detected by analyzing SMTP traffic) will be limited, and the sending will not be possible if the relay server is not available.

### MTA child processes {#mta-child-processes}

It is possible to control the population of child processes (maxSpareServers by default 2) in order to optimize broadcast performance according to the CPU power of the servers and the available network resources. This configuration is to be made in the **`<master>`** section of MTA configuration on each individual computer.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Also refer to [Email sending optimization](../../installation/using/email-deliverability.md#email-sending-optimization).

### Managing outbound SMTP traffic with affinities {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>The affinity configuration needs to be coherent from one server to another. We recommend that you contact Adobe for affinity configuration, as configuration changes should be replicated on all application servers running the MTA.

You can improve outbound SMTP traffic through affinities with IP addresses.

To do this, apply the following steps:

1. Enter the affinities in the **`<ipaffinity>`** section of the **serverConf.xml** file.

   One affinity can have several different names: to separate them, use the **;** character.

   Example:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   To view the relevant parameters, refer to the **serverConf.xml** file.

1. To enable affinity selection in the drop-down lists, you need to add the affinity name(s) in the **IPAffinity** enumeration.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Enumerations are detailed in [this document](../../platform/using/managing-enumerations.md).

   You can then select the affinity to be used, as shown below for typologies:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >You can also refer to [Delivery server configuration](../../installation/using/email-deliverability.md#delivery-server-configuration).

## URL permissions {#url-permissions}

The default list of URLs that can be called by JavaScript codes (workflows, etc.) by your Campaign Classic instances is limited. These are URLs that allow your instances to function properly.

By default, instances are not allowed to connect to outside URLs. However, it is possible to add some outside URLs to the list of authorized URLs, so that your instance can connect to them. This allows you to connect your Campaign instances to outside systems like, for example, SFTP servers or websites in order to enable file and/or data transfer.

Once a URL is added, it is referenced in the configuration file of the instance (serverConf.xml).

They way you can manage URL permissions depends on your hosting model:

* **Hybrid** or **On-premise**: add the URLs to allow into the **serverConf.xml file**. Detailed information is available in the section below.
* **Hosted**: add the URLs to allow via the **Control Panel**. For more information, refer to the [dedicated documentation](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html).

   >[!NOTE]
   >
   >Control Panel is accessible to all Admin users. The steps to grant Admin access to a user are detailed in [this section](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
   >
   >Note that your instance must be hosted on AWS and upgraded with the latest [Gold Standard](../../rn/using/gs-overview.md) build. Learn how to check your version in [this section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). To check if your instance is hosted on AWS, follow the steps detailed in [this page](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

With **Hybrid** and **On-premise** hosting models, the administrator needs to reference a new **urlPermission** in the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

Three connection protection modes exist:

* **Blocking**: all URLs that do not belong to the allowlist are blocked, with an error message. This is the default mode after a postupgrade.
* **Permissive**: all URLs that do not belong to the allowlist are allowed.
* **Warning**: all URLs that do not belong to the allowlist are allowed, but the JS interpreter emits a warning, so that the administrator can collect them. This mode adds JST-310027 warning messages.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>By default, new customers' client use the **blocking mode**. If they need to allow a new URL, they should contact their administrator to add it to the allowlist.
>
>Existing customers coming from a migration can use the **warning mode** for a while. Meanwhile they need to analyze the outbound traffic before authorizing the URLs. Once the list of authorized URLs defined, they should contact their administrator to add the URLs to the allowlist and activate the **blocking mode**.

## Dynamic page security and relays {#dynamic-page-security-and-relays}

By default, all dynamic pages are automatically related to the **local** Tomcat server of the machine whose Web module has started. This configuration is entered in the **`<url>`** section of the query relay configuration for the **ServerConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

To relay execution of the dynamic page on a **remote** server; if the Web module is not activated on the computer. To do this, you must replace the **localhost** with the name of the remote computer for JSP and JSSP, Web applications, reports and strings.

For more on the various parameters available, refer to the **serverConf.xml** configuration file.

For JSP pages, the default configuration is:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign uses the following JSP pages:

* /nl/jsp/**soaprouter.jsp**: client console and Web services connections (SOAP APIs),
* /nl/jsp/**m.jsp**: mirror pages,
* /nl/jsp/**logon.jsp**: Web-based access to reports and to deployment of the client console,
* /nl/jsp/**s.jsp** : Using viral marketing (sponsoring and social networks).

The JSSPs used for the Mobile App Channel are as follows:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Example:**

It's possible to prevent client machine connections from the outside. To do this, simply restrict the execution of **soaprouter.jsp** and only authorize the execution of mirror pages, viral links, web forms and public resources.

The parameters are as follows:

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

In this example, the **`<IP_addresses>`** value coincides with the list of IP addresses (separated by comas) authorized to use the relay module for this mask.

>[!NOTE]
>
>Values shall be adapted according to your configuration and your network constraints, especially if specific configurations have been developed for your installation.

## Restricting authorized external commands {#restricting-authorized-external-commands}

>[!NOTE]
>
>The following configuration is only required for on-premise installations.

From build 8780, technical administrators can restrict the list of authorized external commands that can be used in Adobe Campaign.

To do that, you need to create a text file with the list of commands that you want to prevent from using, for example:

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>This list is not exhaustive.

In the **exec** node of the server configuration file, you need to reference the previously created file in the **blacklistFile** attribute.

**For Linux only**: in the server configuration file, we recommand that you specify a user dedicated to executing external commands to enhance your security configuration. This user is set in the **exec** node of the configuration file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>If no user is specified, all commands are executed in the user context of the Adobe Campaign instance. The user must be different than the user running Adobe Campaign.

For example:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

This user needs to be added to the sudoer list of the 'neolane' Adobe Campaign operator.

>[!IMPORTANT]
>
>You should not use a custom sudo. A standard sudo needs to be installed on the system.

## Managing HTTP headers {#managing-http-headers}

By default, all HTTP headers are not relayed. You can add specific headers in the replies sent by relay. To do this:

1. Go to the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).
1. In the **`<relay>`** node, go to the list of relayed HTTP headers.
1. Add a **`<responseheader>`** element with the following attributes:

    * **name**: header name
    * **value**: value name.

   For example:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Redundant tracking {#redundant-tracking}

When multiple servers are used for redirection, they must be able to communicate with each other via SOAP calls in order to share information from the URLs to be redirected. At the time of delivery start-up, it is possible that not all the redirection servers will be available; therefore they might not have the same level of information.

>[!NOTE]
>
>When using the standard or enterprise architecture, the main application server must be authorized to upload tracking information on each computer.

The URLs of the redundant servers must be specified in the redirection configuration, via the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

**Example:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

The **enableIf** property is optional (empty by default) and allows you to enable the connection only if the result is true; This lets you obtain an identical configuration on all redirection servers.

To obtain the hostname of the computer, run the following command: **hostname -s**.

## Managing public resources {#managing-public-resources}

Public resources are presented in [Managing public resources](../../installation/using/deploying-an-instance.md#managing-public-resources).

They are stored in the **/var/res/instance** directory of the Adobe Campaign installation directory.

The matching URL is: **http://server/res/instance** where **instance** is the name of the tracking instance.

You can specify another directory by adding a node to the **conf-`<instance>`.xml** file to configure storage on the server. This means adding the following lines:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

In this case, the new URL for the public resources given in the upper part of the window of the deployment wizard should point to this folder.

## High availability workflows and affinities {#high-availability-workflows-and-affinities}

You can configure several workflow servers (wfserver) and distribute them on two or more machines. If you choose this type of architecture, configure the connection mode of the load balancers according to the Adobe Campaign access.

For access from the web, select the **load balancer** mode to limit connection times.

If accessing via the Adobe Campaign console, choose **hash** or **sticky ip** mode. This lets you maintain the connection between the rich client and the server and prevent a user session from being interrupted during an import or export operation, for example.

You can choose to force the execution of a workflow or a workflow activity on a particular machine. To do this, you must define one or more affinities for the concerned workflow or activity.

1. Create the affinities of the workflow or activity by entering them in the **[!UICONTROL Affinity]** field.

   You can freely choose the affinity names. Nevertheless, make sure you do not use spaces or punctuation marks. If you use different servers, specify different names.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   The drop-down list contains formerly used affinities. It is completed over time with the different entered values.

1. Open the **nl6/conf/config-`<instance>.xml`** file.
1. Modify the line which matches the **[!UICONTROL wfserver]** module as follows:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   If you define several affinities, they must be separated by commas without any spaces:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   The comma following the name of the affinity is necessary for the execution of workflows for which no affinity is defined.

   If you wish to execute only workflows for which an affinity is defined, do not add a comma at the end of the list of your affinities. For example, modify the line as follows:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Automatic process restart {#automatic-process-restart}

By default, the different Adobe Campaign processes restart automatically at 6am (server time) every day.

However, you can change this configuration.

To do this, go to the **serverConf.xml** file, located in the **conf** repository of your installation. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

Each process configured in this file has a **processRestartTime** attribute. You can modify the value of this attribute to adapt the restart time of each process according to your needs.

>[!IMPORTANT]
>
>Do not delete this attribute. All processes must be restarted every day.

## Limiting uploadable files {#limiting-uploadable-files}

A new attribute **uploadWhiteList** lets you restrict the file types available for upload on the Adobe Campaign server.

This attribute is available within the **dataStore** element of the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

The default value of this attribute is **.+** and it lets you upload any file type.

To limit the possible formats, you must replace the attribute value by a valid java regular expression. You can enter several values by separating them by a comma.

For example: **uploadWhiteList=".&#42;.png,.&#42;.jpg"** will let you upload PNG and JPG formats on the server. No other formats will be accepted.

>[!IMPORTANT]
>
>In Internet Explorer, the complete file path must be verified by the regular expression.

## Proxy connection configuration {#proxy-connection-configuration}

You can connect the Campaign server to an external system through a proxy, using a **File Transfer** workflow activity for example. To achieve this, you need to configure the **proxyConfig** section of the **serverConf.xml** file through a specific command. All parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

The following proxy connections are possible: HTTP, HTTPS, FTP, SFTP. Please note that starting 20.2 Campaign release, the HTTP and HTTPS protocol parameters are **no longer available**. Those parameters are still mentioned below as they remain available in previous builds - including 9032.

>[!CAUTION]
>
>Only the basic authentication mode is supported. NTLM authentication is not supported.
>
>SOCKS proxies are not supported.
>

You can use the following command:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

protocol parameters can be ‘http’, ‘https’ or ‘ftp’.

If you are setting FTP on the same port as HTTP/HTTPS traffic, you can use the following:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

The ‘http’ and ‘https’ options are only used when the protocol parameter is ‘ftp’ and indicate if the tunneling on the specified port will be performed over HTTPS or over HTTP.  

If you use a different ports for FTP/SFTP and HTTP/HTTPS traffic over proxy server, you should set the ‘ftp’ protocol parameter.  


For example:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Then enter the password.

HTTP connections are defined in the proxyHTTP parameter:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS connections are defined in the proxyHTTPS parameter:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS connections are defined in the proxyFTP parameter:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

If you use the same proxy for several connection types, only the proxyHTTP will be defined with useSingleProxy set to "1" or "true".

If you have internal connections that should go through the proxy, add them in the override parameter.

If you want to tempararily disable the proxy connection, set the enabled parameter to "false" or "0".
