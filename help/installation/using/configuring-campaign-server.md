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
# Get started with Campaign server configuration{#gs-campaign-server-config}

This chapter details server-side configurations that can be performed to match your needs and your environment specificities.

## Restrictions

These procedures are restricted to **on-premise**/**hybrid** deployments and require Administration permissions. 

For **hosted** deployments, server-side settings can be configured by Adobe only. However, some settings can be set up within  [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html), such as IP allowlist management or URL permissions. [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

For more information, refer to these sections:

* [Control Panel documentation](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)
* [Hosting models](../../installation/using/hosting-models.md)
* [Campaign Classic On-premise & Hosted capability matrix](../../installation/using/capability-matrix.md)

## Configuration files

Campaign Classic configuration files are stored in the **conf** folder of the Adobe Campaign installation folder. The configuration is spread over two files:

* **serverConf.xml**: general configuration for all instances. This file combines the technical parameters of the Adobe Campaign server: these are shared by all instances. The description of some of these parameters is detailed below. The different nodes and parameters and listed in this [section](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (where **instance** is the name of the instance): specific configuration of the instance. If you share your server among several instances, please enter the parameters specific to each instance in their relevant file.

General server configuration guidelines are detailed in [Campaign server configuration](../../installation/using/configuring-campaign-server.md).


## Configuration scope

Configure or adapt Campaign server depending on your needs and configuration. You can:

* Secure the [Internal identifier](#internal-identifier)
* Enable [Campaign processes](#enabling-processes)
* Configure [URL Permissions](url-permissions.md)
* Define [Security Zones](security-zones.md)
* Configure [Tomcat settings](configure-tomcat.md)
* Customize [Delivery parameters](#delivery-settings)
* Define [Dynamic page security and relays](#dynamic-page-security-and-relays)
* Restrict the list of [Allowed external commands](#restricting-authorized-external-commands)
* Set up [Redundant tracking](#redundant-tracking)
* Manage [High availability and workflow affinities](#high-availability-workflows-and-affinities)
* Configure file management - [Learn more](#file-and-resmanagement)
   * Limit upload files format
   * Enable access to public resources
   * Configure Proxy connection
* [Automatic process restart](#automatic-process-restart)


## Internal identifier {#internal-identifier}

The **internal** identifier is a technical login to be used for installation, administration and maintenance purposes. This login is not associated with an instance.

Operators connected using this login will have all the rights on all instances. This login won't have a password in the case of a new installation. You must manually define this password.

Use the following command:

```
nlserver config -internalpassword
```

The following information is then displayed. Enter and confirm the password:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Enable processes {#enabling-processes}

Adobe Campaign processes on the server are enabled (and disabled) via the **config-default.xml** and **`config-<instance>.xml`** files.

To apply the changes to these files, if the Adobe Campaign service is started, you must run the **nlserver config -reload** command.

There are two types of processes: multi-instance and single instance.

* **multi-instance**: one single process is started for all instances. This is the case for **web**, **syslogd** and **trackinglogd** processes.

  Enablement can be configured from the **config-default.xml** file.

  Declaring an Adobe Campaign server to access client consoles and for redirection (tracking):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  In this example, the file is edited using a **vi** command in Linux. It can be edited using any **.txt** or **.xml** editor.

* **mono-instance**: one process is started for each instance (modules: **mta**, **wfserver**, **inMail**, **sms** and **stat**).

  Enablement can be configured using the configuration file of the instance:

  ```
  config-<instance>.xml
  ```

  Declaring a server for delivery, executing workflow instances and recovering bounce mail:

  ```
  <mta autoStart="true" statServerAddress="localhost"/>
  <wfserver autoStart="true"/>  
  <inMail autoStart="true"/>
  <stat autoStart="true"/>
  ```

**Campaign data storage**

You can configure the storage directory (**var** directory) of Adobe Campaign data (logs, downloads, redirections, etc.). To do this, use the **XTK_VAR_DIR** system variable:

* In Windows, indicate the following value value in the **XTK_VAR_DIR** system variable

  ```
  D:\log\AdobeCampaign
  ```

* In Linux, go to the **customer.sh** file and indicate: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  For more on this, refer to [Personalize parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Configure delivery settings {#delivery-settings}

The delivery parameters must be configured in the **serverConf.xml** folder.

* **DNS configuration**: specify the delivery domain and the IP addresses (or host) of the DNS servers used to respond to MX-type DNS queries made by the MTA module from the **`<dnsconfig>`** onwards.

  >[!NOTE]
  >
  >The **nameServers** parameter is essential for an installation in Windows. For an installation in Linux, it must be left empty.

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

You can also carry out the following configurations depending on your needs and settings: configure a [SMTP relay](#smtp-relay), adapt the number of [MTA child processes](#mta-child-processes), [Manage outbound SMTP traffic](#managing-outbound-smtp-traffic-with-affinities).

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

It is possible to control the number of child processes (maxSpareServers by default 2) in order to optimize broadcast performance according to the CPU power of the servers and the available network resources. This configuration is to be made in the **`<master>`** section of MTA configuration on each individual computer.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Also refer to [Email sending optimization](../../installation/using/email-deliverability.md#email-sending-optimization).

### Manage outbound SMTP traffic with affinities {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>The affinity configuration needs to be consistent from one server to another. We recommend that you contact Adobe for affinity configuration, as configuration changes should be replicated on all application servers running the MTA.

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



## Dynamic page security and relays {#dynamic-page-security-and-relays}

By default, all dynamic pages are automatically related to the **local** Tomcat server of the machine whose Web module has started. This configuration is entered in the **`<url>`** section of the query relay configuration for the **ServerConf.xml** file. 

You can relay execution of the dynamic page on a **remote** server; if the Web module is not activated on the computer. To do this, you must replace the **localhost** with the name of the remote computer for JSP and JSSP, Web applications, reports and strings.

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

### Manage HTTP headers {#managing-http-headers}

By default, all HTTP headers are not relayed. You can add specific headers in the replies sent by relay. To do this:

1. Go to the **serverConf.xml** file.
1. In the **`<relay>`** node, go to the list of relayed HTTP headers.
1. Add a **`<responseheader>`** element with the following attributes:

    * **name**: header name
    * **value**: value name.

   For example:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Restrict authorized external commands {#restricting-authorized-external-commands}

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


## Redundant tracking {#redundant-tracking}

When multiple servers are used for redirection, they must be able to communicate with each other via SOAP calls in order to share information from the URLs to be redirected. At the time of delivery start-up, it is possible that not all the redirection servers will be available; therefore they might not have the same level of information.

>[!NOTE]
>
>When using the standard or enterprise architecture, the main application server must be authorized to upload tracking information on each computer.

The URLs of the redundant servers must be specified in the redirection configuration, via the **serverConf.xml** file.

**Example:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

The **enableIf** property is optional (empty by default) and allows you to enable the connection only if the result is true. This lets you obtain an identical configuration on all redirection servers.

To obtain the hostname of the computer, run the following command: **hostname -s**.

## File and resource management{#file-and-resmanagement}

### Limit upload file format {#limiting-uploadable-files}

Use the **uploadWhiteList** attribute to restrict the file types available for upload on the Adobe Campaign server.

This attribute is available within the **dataStore** element of the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

The default value of this attribute is **.+** and lets you upload any file type.

To limit the possible formats, replace the attribute value by a valid java regular expression. You can enter several values by separating them by a comma.

For example: **uploadWhiteList=".&#42;.png,.&#42;.jpg"** will let you upload PNG and JPG formats on the server. No other formats will be accepted.

>[!NOTE]
>
>In Internet Explorer, the complete file path must be verified by the regular expression.

You can also prevent important files from being uploaded by configuring the Web Server. [Learn more](web-server-configuration.md)

### Proxy connection configuration {#proxy-connection-configuration}

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

### Manage public resources {#managing-public-resources}

To be publicly available, the images used in emails and public resources linked to campaigns must be present on an externally accessible server. They can then be available to external recipients or operators. [Learn more](../../installation/using/deploying-an-instance.md#managing-public-resources).

Public resources are stored in the **/var/res/instance** directory of the Adobe Campaign installation directory.

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

   You can choose any affinity name, but make sure you do not use spaces or punctuation marks. If you use different servers, specify different names.

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

## Automatic restart {#automatic-process-restart}

By default, the different Adobe Campaign processes restart automatically at 6am (server time) every day.

However, you can change this configuration.

To do this, go to the **serverConf.xml** file, located in the **conf** repository of your installation.

Each process configured in this file has a **processRestartTime** attribute. You can modify the value of this attribute to adapt the restart time of each process according to your needs.

>[!IMPORTANT]
>
>Do not delete this attribute. All processes must be restarted every day.
