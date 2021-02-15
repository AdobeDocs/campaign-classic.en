---
solution: Campaign Classic
product: campaign
title: Campaign server configuration
description: Campaign server configuration
audience: installation
content-type: reference
topic-tags: initial-configuration
---

# Campaign server configuration{#campaign-server-configuration}

The following sections details mandatory server configurations which will guarantee the efficient operating of Adobe Campaign for most set-ups.

Additional configurations are offered in [Configure Campaign server](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Server side configurations can only be performed by Adobe for deployments hosted by Adobe. To learn more about the different deployments, refer to the [Hosting models](../../installation/using/hosting-models.md) section or to [the capability matrix](../../installation/using/capability-matrix.md).

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

## Configuration files {#configuration-files}

The configuration files are stored in the **conf** folder of the Adobe Campaign installation folder. The configuration is spread over two files:

* **`config-<instance>.xml`** (where **instance** is the name of the instance): specific configuration of the instance. If you share your server among several instances, please enter the parameters specific to each instance in their relevant file.
* **serverConf.xml**: general configuration for all instances. This file combines the technical parameters of the Adobe Campaign server: these are shared by all instances. The description of some of these parameters is detailed below. Refer to the file itself to view all available parameters. The different nodes and parameters and listed in this [section](../../installation/using/the-server-configuration-file.md).

You can configure the storage directory (**var** directory) of Adobe Campaign data (logs, downloads, redirections, etc.). To do this, use the **XTK_VAR_DIR** system variable:

* In Windows, indicate the following value value in the **XTK_VAR_DIR** system variable

  ```
  D:\log\AdobeCampaign
  ```

* In Linux, go to the **customer.sh** file and indicate: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Enabling processes {#enabling-processes}

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

## Delivery settings {#delivery-settings}

The delivery parameters must be configured in the **serverConf.xml** folder.

* **DNS configuration**: specify the delivery domain and the IP addresses (or host) of the DNS servers used to respond to MX-type DNS queries made by the MTA module from the **`<dnsconfig>`** onwards.

  >[!NOTE]
  >
  >The **nameServers** parameter is essential for an installation in Windows. For an installation in Linux, it must be left empty.

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

The other delivery parameters available in this file are presented in [Personalizing delivery parameters](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Also refer to [Email deliverability](../../installation/using/email-deliverability.md).
