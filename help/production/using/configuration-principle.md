---
title: Configuration principle
seo-title: Configuration principle
description: Configuration principle
seo-description: 
page-status-flag: never-activated
uuid: a2e520bf-0560-4198-9f05-6a3496b45567
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 6cb915cd-29af-4c32-a237-0b3b111603a1
index: y
internal: n
snippet: y
---

# Configuration principle{#configuration-principle}

The Adobe Campaign platform is based on the concept of instances, similar to that of virtual hosts used by Apache. This mode of operation lets you share a server by assigning several instances to it. Instances are completely separate from each other and operate with their own database and configuration file.

For a given server, there are two elements that are common to all Adobe Campaign instances:

* The **internal** password: this is the general administrator password. It is common to all instances of a particular application server.

  >[!CAUTION]
  >
  >To log on with the **Internal** identifier, you need to have defined a password beforehand. For more on this, refer to [this section](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Multiple technical server configurations: these configurations can all be overloaded in the specific configuration of an instance.

The configuration files are saved in the **conf** directory of the installation directory. The configuration is broken down into three files:

* **serverConf.xml**: overall configuration for all instances.
* **config-**`<instance>`**.xml** (where **`<instance>`** is the instance name): specific configuration of an instance.
* **serverConf.xml.diff**: delta between the initial configuration and the current configuration. This file is generated automatically by the application and must not be modified manually. It is used to automatically propagate user modifications when updating a build version.

An instance configuration is loaded as follows:

* The module loads the **serverConf.xml** file to obtain the parameters shared by all instances.
* It then loads the **config-**`<instance>`**.xml** file. The values found in this file have priority over values contained in **serverConf.xml**.

  These two files have the same format. Any value in **serverConf.xml** can be overloaded for a given instance in the **config-`<instance> .xml</instance>`** file.

This operating mode provides great flexibility for configurations.
