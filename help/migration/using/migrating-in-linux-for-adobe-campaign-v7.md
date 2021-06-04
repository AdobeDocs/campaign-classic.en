---
product: campaign
title: Migrating in Linux for Adobe Campaign v7
description: Migrating in Linux for Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
---
# Migrating in Linux for Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## General procedure {#general-procedure}

Migration steps in Linux are as follows:

1. Stop services: see [Service stop](#service-stop).
1. Save the database: see [Back up the database and the existing installation](#back-up-the-database-and-the-existing-installation).
1. Uninstall previous Adobe Campaign version packages: see [Uninstalling Adobe Campaign previous version packages](#uninstalling-adobe-campaign-previous-version-packages).
1. Migrate the platform: refer to [Deploying Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Re-start service: refer to [Re-starting services](#re-starting-services).

## Service stop {#service-stop}

First, stop all processes with access to the database on all machines concerned.

1. Log in as **root**.
1. All servers which use the redirection module (**webmdl** service) need to be stopped. For Apache, run the following command:

   ```
   /etc/init.d/apache2 stop
   ```

1. Log in again as **root**.
1. Stop Adobe Campaign previous version services on all servers.

   ```
   /etc/init.d/nlserver6 stop
   ```

   If you are migrating from v5.11, run the following command:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Make sure Adobe Campaign services are stopped on each server.

   ```
   ps waux | grep nlserver
   ```

   The list of active processes is displayed along with their ID (PID).

1. If one or more Adobe Campaign processes are still active or blocked after a few minutes, kill them.

   ```
   killall nlserver
   ```

1. If some processes are still active after a few minutes, you can force them to close using the command:

   ```
   killall -9 nlserver
   ```

## Back up the database and the existing installation {#back-up-the-database-and-the-existing-installation}

The procedure depends on your Adobe Campaign previous version.

### Migrating from Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl5** directory using the following command:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl5.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl5.back** folder), to prevent the **mta**, **wfserver**, **stat** etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migrating from Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl6** directory using the following command:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl6.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl6.back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migrating from Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Make a backup of the Adobe Campaign database.
1. Log in as **neolane** and make a backup of the **nl6** directory using the following command:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl6.back** folder and save it to a secure location other than the server.

## Uninstalling Adobe Campaign previous version packages {#uninstalling-adobe-campaign-previous-version-packages}

The procedure depends on your Adobe Campaign previous version.

### Uninstalling Adobe Campaign v5 packages {#uninstalling-adobe-campaign-v5-packages}

1. Log in as **root**.
1. Identify the Adobe Campaign packages installed using the following command.

    * In **Debian**:

      ```    
      dpkg -l | grep nl
      ```    
    
      The list of installed packages is displayed:

      ```    
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

    * In **Red Hat**:

      ```    
      rpm -qa | grep nl
      ```

1. Uninstall Adobe Campaign v5 packages.

    * In **Debian**:

      ```    
      dpkg --purge nlserver5 nlthirdparty5
      ```

    * In **Red Hat**:

      ```    
      rprm -ev nlserver5 nlthirdparty5
      ```

### Uninstalling Adobe Campaign v6 packages {#uninstalling-adobe-campaign-v6-packages}

This section shows how to uninstall Adobe Campaign v6.02 or v6.1 packages.

1. Log in as **root**.
1. Identify the Adobe Campaign packages installed using the following command.

    * In **Debian**:

      ```    
      dpkg -l | grep nl
      ```    
    
      The list of installed packages is displayed:

      ```    
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

    * In **Red Hat**:

      ```    
      rpm -qa | grep nl
      ```

1. Uninstall Adobe Campaign v6 packages.

    * In **Debian**:

      ```    
      dpkg --purge nlserver6 nlthirdparty6
      ```

    * In **Red Hat**:

      ```    
      rprm -ev nlserver6 nlthirdparty6
      ```

## Deploying Adobe Campaign v7 {#deploying-adobe-campaign-v7}

The procedure depends on your Adobe Campaign previous version.

### Migrating from Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >When migrating from v5.11, Adobe Campaign is installed in the **/usr/local/neolane/nl6/** directory by default.
   >
   >Once the packages are installed, the following message is displayed: **'WdbcTimeZone' option is missing**. This is normal.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Modify the **.bashrd** file which matches the **neolane** user. Log on as **neolane** and run the following command:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >When you log in as **neolane**, the following message is displayed: **nl5/env.sh : No such file or directory**. This is normal.

   At the end of the file, replace **nl5/env.sh** with **nl6/env.sh**.

1. Log in as **root** and prepare the instance using the following commands:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >These commands let you create the Adobe Campaign v6 internal files system: **conf** directory (with the **config-default.xml** and **serverConf.xml** files), **var** directory.

1. Go to the **nl5.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   >[!IMPORTANT]
   >
   >For the first command below, do not copy the **config-default.xml** file.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. In the Adobe Campaign v7 **serverConf.xml** and **config-default.xml** files, apply the specific configurations that you had for Adobe Campaign v5. For the **serverConf.xml** file, use the **nl5/conf/serverConf.xml.diff** file.

   >[!NOTE]
   >
   >When reporting configurations from Adobe Campaign v5 to Adobe Campaign v7, make sure the paths to the physical directories lead to Adobe Campaign v7 and not Adobe Campaign v5.

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >You must specify which timezone to use as a reference during the postupgrade (using the **-timezone** option). In this case, we are using the Europe/Paris timezone **-timezone: "Europe/Paris"**.

   >[!NOTE]
   >
   >We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

>[!IMPORTANT]
>
>Do not start Adobe Campaign services yet: changes still need to be made in Apache.

### Migrating from Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >Adobe Campaign v7 is installed in the same directory by default as Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Go to the **nl6.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >The "multi timezone" mode was only available in v6.02 for PostgreSQL database engines. It is now available no matter what version of database engine is being used. We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

### Migrating from Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >Adobe Campaign v7 is installed in the **/usr/local/neolane/nl6/** directory by default.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Go to the **nl6.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migrating the redirection server (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

At this stage, Apache needs to be stopped. Refer to: [Service stop](#service-stop).

1. Log in as **root**.
1. Change the Apache environment variables to make them link to the **nl6** directory.

    * In **Debian**:

      ```    
      vi /etc/apache2/envvars
      ```

    * In **Red Hat**:

      ```    
      vi /usr/local/apache2/bin/envvars
      ```

1. Then run the following commands:

    * In **Debian**:

      In the **nlsrv.load** file, replace **nl5** with **nl6**.

      ```    
      vi /etc/apache2/mods-available/nlsrv.load
      ```    
    
      Delete the link of the **nlsrv.conf** file and create a new one.

      ```    
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

    * In **Red Hat**:

      Go to the **/usr/local/apache2/conf** directory, edit the **http.conf** file and replace **nl5** with **nl6** in the following lines.

      In **RHEL 7/Debian 8**:

      ```    
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Go to the **alias.conf** file and replace all **nl5** with **nl6**. To do this in Debian, run the following command:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. For more information, refer to [Security](../../migration/using/general-configurations.md#security).

## Re-starting services {#re-starting-services}

The procedure depends on your Adobe Campaign previous version.

### Migrating from Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Before going on to the next step, run a full test of the new installation, make sure there are no regressions and that everything works by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

### Migrating from Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Fully test the new installation, check that it does not regress and make sure that everything is working correctly by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

### Migrating from Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Fully test the new installation, check that it does not regress and make sure that everything is working correctly by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

## Deleting and cleansing Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

Delete the **nl5.back** directory. Log in as **neolane** and run the following command:

```
su - neolane
rm -rf nl5.back
```

Re-start the server.
