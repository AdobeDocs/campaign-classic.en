---
product: campaign
title: Installing packages with Linux
description: Installing packages with Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
---
# Installing packages with Linux{#installing-packages-with-linux}

![](../../assets/v7-only.svg)

For a Linux 32 bit platform, install Adobe Campaign 32 bit. For a Linux 64 bit platform, install Adobe Campaign 64 bit.

For each of these versions, Adobe Campaign comes with one package: **nlserver**. This package contains the binaries and configuration files for a given version.

The installation commands enables you to:

* Copy the files to **/usr/local/neolane**
* Create an Adobe Campaign Linux account (and the associated group), which is created with **/usr/local/neolane** as its home directory
* Create an automatic script **/etc/init.d/nlserver6** for use at startup, or create a systemd unit (starting 20.1).

>[!NOTE]
>
>The **neolane** system user must not have been created before the command was run. The **neolane** user is created automatically during installation.
>
>The **home** directory linked to the **neolane** user is also created automatically in **[!UICONTROL /usr/local/neolane]**. Please make sure there is sufficient space on the **[!UICONTROL /usr/local]** disk (several GB).

You can run the **ping `hostname`** command to make sure the server can reach itself.

## Distribution based on RPM packages {#distribution-based-on-rpm--packages}

To install Adobe Campaign onto an RPM (RHEL, CentOS and SUSE) operating system, apply the following steps:

1. You must first obtain the Adobe Campaign package.

   The file is named as below, where **XXXX** is the Adobe Campaign build number:

    * **nlserver6-v7-XXXX-0.x86_64.rpm** for v7.
    * **nlserver6-XXXX-0.x86_64.rpm** for v6.1.

   >[!CAUTION]
   >
   >Make sure you use the correct file name for your version of Adobe Campaign in the command samples of this section.

1. To install it, connect as **root** and execute the following command (where **XXXX** is the Adobe Campaign build number):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   The rpm file has dependencies on packages that you can find on CentOS/Red Hat distributions. If you don't want to use some of these dependencies (for example, if you want to use Oracle JDK instead of OpenJDK), you may have to use the "nodeps" option of rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

The 'bc' command, necessary for executing the netreport (refer to [this section](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) for more information), is not available by default on all Linux distributions. To check whether the command is available, run the 'which bc' command. If not, you have to install it.

With CentOS, you must install the bc.x86_64 package: connect as **root** and run the following command:

```
yum install bc.x86_64
```

## Distribution based on APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 64 bits {#in-debian-64-bits}

To install Adobe Campaign 64 bit on a Debian 64 bit operating system, apply the following steps:

1. You must first obtain the Adobe Campaign package.

    * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** for v7.
    * **nlserver6-XXXX-linux-2.6-amd64.deb** for v6.1.

   **XXXX** is the Adobe Campaign build number.

   >[!CAUTION]
   >
   >Make sure you use the correct file name for your version of Adobe Campaign in the command samples of this section.

1. To install it, connect as **root** and execute the following command (where **XXXX** is the Adobe Campaign build number):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   If there are missing dependenciess, run the following command: 

   ```
   apt-get install -f
   ```

**Debian 8/9 specifics**

When installing Adobe Campaign on a Debian 8/9 operating system, consider the following:

* OpenSSL must be installed beforehand.
* Install libicu52 (Debian 8) or libicu57 (Debian 9), libprotobuf9 (Debian8) and libc-ares2 with the following commands:

  ```
  aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
  ```

  ```
  aptitude install libc-ares2
  ```

  ```
  aptitude install libprotobuf9 (only Debian 8)
  ```

* Install JDK7 with the following command:

  ```
  aptitude install openjdk-7-jdk (Debian 8)
  ```

  ```
  aptitude install openjdk-7-jdk (Debian 9)
  ```

## Personalizing parameters {#personalizing-parameters}

Some parameters can be personalized via the **customer.sh** file

If you are performing the installation for the first time, the **customer.sh** file might not yet exist on the server. Create it and make sure it has execution rights. If this is not the case, enter the following command:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Server encoding {#server-encoding}

By default, the server is started in an iso8859-15 enviornment. Nevertheless, the server can be started in an UTF-8 environment.

   >[!CAUTION]
   >
   >This change impacts the interactions with the file system (files loaded via a workflow or a JavaScript script) and on the file encoding. We therefore recommend using the default environment.

Nevertheless, for creating a **Japanese instance**, you must use a UTF-8 environment.

To enable the UTF-8 environment, use the following command:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Default language for the server {#default-language-for-the-server}

The installation supports both English and French. English is used by default.

To switch to French, enter the following commands:

```
su - neolane
vi nl6/customer.sh
```

and add the following line:

```
export neolane_LANG=fra
```

To ensure that system messages are correctly read, the consoles must be in a code page corresponding to the language (ISO-8859-1 or -15 for French).

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

      Default values for OOO_INSTALL_DIR, OOO_BASIS_INSTALL_DIR, OOO_URE_INSTALL_DIR are provided. You can override them in **customer.sh** if your layout of the LibreOffice installation is different:

      ```    
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

    * CentOs

      Use the following default values:

      ```    
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* For Java Development Kit (JDK):

  By default, the configuration script of the Adobe Campaign environment (`~/nl6/env.sh`) searches for the JDK installation directory. Since this behavior is not 100% reliable, you need to specify which JDK needs to be used. To do this, you can force the **JDK_HOME** environment variable using the following command:

  ```
  export JDK_HOME=/usr/java/jdk1.6.0_07
  ```

  >[!NOTE]
  >
  >This is an example. Make sure that the JDK version used matches the directory name.

  To test the JDK configuration, log in as the Adobe Campaign system user with the following command:

  ```
  su - neolane
  ```

You must restart the Adobe Campaign service in order for the changes to be taken into account.

The commands are as follows:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

Starting 20.1, we recommend using the following commands instead:

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

  Refer to [Environment variables](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Configuration for Adobe Campaign

  To finalize the installation of the Oracle client for Adobe Campaign, you need to create a symbolic link for the **.so** file used by Adobe Campaign.

  To do this, use the following commands:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

If you encounter a problem, make sure the packages listed in the [Oracle installation documentation](https://www.oracle.com/pls/db112/portal.portal_db?selected=11) are correctly installed.

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

```
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

```
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

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Password for the internal identifier {#password-for-the-internal-identifier}

The Adobe Campaign server defines a technical login called **internal** that has all rights on all instances. Just after installation the login does not have a password. It is mandatory to define one.

Learn more in [this section](../../installation/using/configuring-campaign-server.md#internal-identifier).
