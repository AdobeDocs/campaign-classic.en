---
solution: Campaign Classic
product: campaign
title: File and resource management
description: Learn how to configure file and resource management in Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
---
# File and resource management{#file-and-resmanagement}

## Limit upload file format {#limiting-uploadable-files}

Use the **uploadWhiteList** attribute to restrict the file types available for upload on the Adobe Campaign server.

This attribute is available within the **dataStore** element of the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

The default value of this attribute is **.+** and lets you upload any file type.

To limit the possible formats, replace the attribute value by a valid java regular expression. You can enter several values by separating them by a comma.

For example: **uploadWhiteList=".&#42;.png,.&#42;.jpg"** will let you upload PNG and JPG formats on the server. No other formats will be accepted.

>[!NOTE]
>
>In Internet Explorer, the complete file path must be verified by the regular expression.

You can also prevent important files from being uploaded by configuring the Web Server. [Learn more](web-server-configuration.md)

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

## Manage public resources {#managing-public-resources}

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
