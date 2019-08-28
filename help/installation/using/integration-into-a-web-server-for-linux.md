---
title: Integration into a Web server for Linux
seo-title: Integration into a Web server for Linux
description: Integration into a Web server for Linux
seo-description: 
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
index: y
internal: n
snippet: y
---

# Integration into a Web server for Linux{#integration-into-a-web-server-for-linux}

Adobe Campaign includes Apache Tomcat which acts as the entry point in the application server via HTTP (and SOAP).

You can use this integrated Tomcat server to serve HTTP requests.

In this case:

* the default listening port is 8080. To change it, refer to [Configuring Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* The client consoles then connect using a URL such as:

  ```
  http://<computer>:8080
  ```

However, for security and administration reasons, we recommend using a dedicated Web server as the main entry point for HTTP traffic when the computer that is running Adobe Campaign is exposed on the Internet and you wish to open access to the console outside of your network.

A Web server also lets you guarantee data confidentiality with the HTTPs protocol.

Likewise, you must use a Web server when you wish to use the tracking functionality, which is only available as an extension module to a Web server.

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

   In Debian 7:

   ```
   LoadModule requesthandler22_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

   In Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Create the file **nlsrv.conf** in **/etc/apache2/mods-available** using the following command:

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
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

