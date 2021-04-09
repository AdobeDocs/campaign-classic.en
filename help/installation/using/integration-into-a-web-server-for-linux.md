---
solution: Campaign Classic
product: campaign
title: Integration into a Web server for Linux
description: Learn how to integrate Campaign into a Web server (Linux)
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
---
# Integration into a Web server for Linux{#integration-into-a-web-server-for-linux}

Adobe Campaign includes Apache Tomcat which acts as the entry point in the application server via HTTP (and SOAP).

You can use this integrated Tomcat server to serve HTTP requests.

In this case:

* the default listening port is 8080. To change it, refer to [this section](configure-tomcat.md).
* The client consoles then connect using a URL such as:

  ```
  http://<computer>:8080
  ```

However, for security and administration reasons, we recommend using a dedicated Web server as the main entry point for HTTP traffic when the computer that is running Adobe Campaign is exposed on the Internet and you wish to open access to the console outside of your network.

A Web server also lets you guarantee data confidentiality with the HTTPs protocol.

Likewise, you must use a Web server when you wish to use the tracking functionality, which is only available as an extension module to a Web server.

>[!NOTE]
>
>If you do not use the tracking functionality, you can perform a standard installation of Apache or IIS with a redirection to Campaign. The tracking Web server extension module is not required.

## Configuring the Apache Web server with Debian {#configuring-the-apache-web-server-with-debian}

This process applies if you have installed Apache under a distribution based on APT.

Apply the following steps:

1. Disable the modules loaded by default using the following command:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Ensure that the **alias**, **authz_host** and **mime** modules are still enabled. To do this, use the following command:

   ```
   a2enmod  alias authz_host mime
   ```

1. Create the file **nlsrv.load** in **/etc/apache2/mods-available** and insert the following content:

   In Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Create the file **nlsrv.conf** in **/etc/apache2/mods-available** using the following command:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Activate this module with the following command:

   ```
    a2enmod nlsrv
   ```

   If you are using the **mod_rewrite** module for Adobe Campaign pages, you need to rename the **nlsrv.load** and **nlsrv.conf** files to **zz-nlsrv.load** and **zz-nlsrv.conf**. To activate the module, run the following command:

   ```
   a2enmod zz-nlsrv
   ```

1. Edit the **/etc/apache2/envvars** file, add the following lines:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Save the changes.

1. Then add Adobe Campaign users to the Apache user group and vice versa using the following type of command:

    ```
    usermod neolane -G www-data
    usermod www-data -G neolane
    ```

1. Restart Apache:

    ```
    invoke-rc.d apache2 restart
    ```

## Configuring Apache web server in RHEL {#configuring-apache-web-server-in-rhel}

This procedure applies if you have installed and secured Apache under a RPM (RHEL, CentOS and Suse) based package.

Apply the following steps:

1. In the `httpd.conf` file, activate the following Apache modules:

    ```
    alias
    authz_host
    mime
    ```

1. Deactivate the following modules:

    ```
    auth_basic
    authn_file
    authz_default
    authz_user
    autoindex
    cgi
    dir
    env
    negotiation
    userdir
    ```

   Comment the functions linked to deactivated modules:

    ```
    DirectoryIndex
    IndexOptions    
    AddIconByEncoding    
    AddIconByType    
    AddIcon    
    DefaultIcon    
    ReadmeName    
    HeaderName    
    IndexIgnore    
    LanguagePriority    
    ForceLanguagePriority
    ```

1. Create an Adobe Campaign specific configuration file in the `/etc/httpd/conf.d/` folder. For example `CampaignApache.conf`

1. For **RHEL7**, add the following instructions in the file:

    ```
    LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
    Include /usr/local/neolane/nl6/conf/apache_neolane.conf
    ```

1. For **RHEL7**:

   Add the `/etc/systemd/system/httpd.service` file with the following content:

    ```
    .include /usr/lib/systemd/system/httpd.service
    
    [Service]
    Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
    ```

   Update the module used by systemd:

    ```
    systemctl daemon-reload
    ```

1. Then add Adobe Campaign operators into the Apache operators group and vice-versa, by running the command:

    ```
    usermod -a -G neolane apache
    usermod -a -G apache neolane
    ```

   The group names to use depend on the way Apache is configured.

1. Run Apache and the Adobe Campaign server.

   For RHEL7:

    ```
    systemctl start httpd
    systemctl start nlserver
    ```

## Launching the Web server and testing the configuration{#launching-the-web-server-and-testing-the-configuration}

You can now test the configuration by starting Apache. The Adobe Campaign module should now display its banner on the console (two banners on certain operating systems):

```
 /etc/init.d/apache start
```

The following information is displayed:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Next check that it responds by submitting a test URL.

You can test this from the command line by executing:

```
 telnet localhost 80  
```

You should obtain:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

Then enter:

```
GET /r/test
```

The following information is displayed:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

You can also request the URL [`https://<computer>`](https://myserver.adobe.com/r/test) from a Web browser.
