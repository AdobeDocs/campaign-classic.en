---
product: campaign
title: Installing packages with Linux
description: Installing packages with Linux
feature: Installation, Application Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
---
# Installing packages with Linux{#installing-packages-with-linux}

Adobe Campaign comes with the **nlserver** package which contains the binaries and configuration files for a given version.

The installation commands enables you to:

* Copy the files to **/usr/local/neolane**
* Create an Adobe Campaign Linux account (and the associated group), which is created with **/usr/local/neolane** as its home directory
* Create an automatic script **/etc/init.d/nlserver6** for use at startup, or create a systemd unit

>[!NOTE]
>
>The **neolane** system user must not have been created before the command was run. The **neolane** user is created automatically during installation.
>
>The **home** directory linked to the **neolane** user is also created automatically in **[!UICONTROL /usr/local/neolane]**. Please make sure there is sufficient space on the **[!UICONTROL /usr/local]** disk.

You can run the **ping `hostname`** command to make sure the server can reach itself.

## Distribution based on RPM packages {#distribution-based-on-rpm--packages}

To install Adobe Campaign onto an RPM (RHEL, CentOS) operating system, follow these steps:

1. Get the Adobe Campaign package. The name of the file is **nlserver6-v7-XXXX-0.x86_64.rpm**, where **XXXX** is the Adobe Campaign build number.

   >[!CAUTION]
   >
   >Make sure you use the correct file name for your version of Adobe Campaign in the command samples of this section.

1. To install it, connect as **root** and execute the following command, where **XXXX** is the Adobe Campaign build number:

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   The rpm file has dependencies on packages that you can find on CentOS/Red Hat distributions. If you don't want to use some of these dependencies (for example, if you want to use Oracle JDK instead of OpenJDK), you may have to use the "nodeps" option of rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

The `bc` command, mandatory for executing the [netreport](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), is not available by default on all Linux distributions. To check whether the command is available, run the `which bc` command. If not, you have to install it.

With CentOS, you must install the bc.x86_64 package: connect as **root** and run the following command:

```
yum install bc.x86_64
```

## Distribution based on APT (Debian) {#distribution-based-on-apt--debian-}

To install Adobe Campaign on a Debian 64 bit operating system, apply the following steps:

1. Get the Adobe Campaign package. The name of the file is **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, where **XXXX** is the Adobe Campaign build number.

   >[!CAUTION]
   >
   >Make sure you use the correct file name for your version of Adobe Campaign in the command samples of this section.

1. To install it, connect as **root** and execute the following command, where **XXXX** is the Adobe Campaign build number:

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   If there are missing dependencies, run the following command: 

   ```
   apt-get install -f
   ```


1. When installing Adobe Campaign on a Debian operating system, consider the following:

  * OpenSSL must be installed beforehand.
  * Install libicu and libc-aresYY, where XX is the version, with the following commands:

    ```
    apt install libicuXX
    ```

    ```
    apt install libc-aresXX
    ```

    ```
    apt install openjdk-XX-jdk
    ```

## Personalizing parameters {#personalizing-parameters}

Some parameters can be personalized via the **customer.sh** file

If you are performing the installation for the first time, the **customer.sh** file might not yet exist on the server. 

Create it and make sure it has execution rights. If this is not the case, enter the following command:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Server encoding {#server-encoding}

By default, the server is started in an iso8859-15 environment. Nevertheless, the server can be started in an UTF-8 environment.

>[!CAUTION]
>
>This change impacts the interactions with the file system (files loaded via a workflow or a JavaScript script) and on the file encoding. We therefore recommend using the default environment.

To create a **Japanese instance**, you must use a UTF-8 environment.

To enable the UTF-8 environment, use the following command:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Environment variables {#environment-variables}

The following environment variables must be defined correctly.

Certain combinations require changes to the environment used for executing Adobe Campaign. A specific file (`/usr/local/neolane/nl6/customer.sh`) can be created and edited to add modifications specific to the Adobe Campaign environment.

If necessary, edit the **customer.sh** file using the **vi customer.sh** command and adapt the configuration or add missing lines:

* For the Oracle client:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  The content of the ORACLE_HOME environment variable matches the Oracle installation directory.

  The content of the TNS_ADMIN variable has to match the location of the **tnsnames.ora** file.

* For LibreOffice:

  To run Adobe Campaign on an existing version of LibreOffice, additional configurations are required: you need to specify the access paths to the installation directory. For instance:

    * Debian

      Default values for OOO_INSTALL_DIR and OOO_BASIS_INSTALL_DIR are provided. You can override them in **customer.sh** if your layout of the LibreOffice installation is different:

      ```    
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      ```

    * CentOs

      Use the following default values:

      ```    
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      ```

* For Java Development Kit (JDK):

  By default, the configuration script of the Adobe Campaign environment (`~/nl6/env.sh`) searches for the JDK installation directory. However, it is recommended to specify which JDK needs to be used. To do this, you can force the **JDK_HOME** environment variable using the following command:

  ```
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >Make sure that the JDK version used matches the directory name.

  To test the JDK configuration, log in as the Adobe Campaign system user with the following command:

  ```
  su - neolane
  ```

You must restart the Adobe Campaign service in order for the changes to be taken into account.

The commands are as follows:

```
systemctl stop nlserver
systemctl start nlserver
```

### Oracle Client in Linux {#oracle-client-in-linux}

When using Oracle with Adobe Campaign, you need to configure the Oracle client layers in Linux.

* Use the full client
* TNS definition

  The TNS definitions must be added during the installation phase. To do this, use the following commands:

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Environment variables

  Refer to [Environment variables](#environment-variables).

* Configuration for Adobe Campaign

  To finalize the installation of the Oracle client for Adobe Campaign, you need to create a symbolic link for the **.so** file used by Adobe Campaign.

  To do this, use the following commands:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

In case of an issue, make sure the packages listed in the Oracle installation documentation are correctly installed.

## Installation checks {#installation-checks}

You can now perform an initial installation test using the following commands:

```
su - neolane
nlserver pdump
```

When Adobe Campaign is not started, the response is:

```
no task
```

## First start-up of the server {#first-start-up-of-the-server}

Once the installation test is complete, enter the following command:

```
nlserver web
```

The following information is then displayed:

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

These commands let you create **config-default.xml** and **serverConf.xml** configuration files. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).

Press **Ctrl+C** to stop the process, then enter the following command:

```
nlserver start web
```

The following information is then displayed:

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

To stop it, enter:

```
nlserver stop web
```

The following information is then displayed:

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Password for the internal identifier {#password-for-the-internal-identifier}

The Adobe Campaign server defines a technical login called **internal** that has all rights on all instances. Just after installation the login does not have a password. It is mandatory to define one.

Learn more in [this section](../../installation/using/configuring-campaign-server.md#internal-identifier).
