---
title: Prerequisites of Campaign installation in Linux
seo-title: Prerequisites of Campaign installation in Linux
description: Prerequisites of Campaign installation in Linux
seo-description: 
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
---

# Prerequisites of Campaign installation in Linux{#prerequisites-of-campaign-installation-in-linux}

## Software prerequisites {#software-prerequisites}

This section details the preliminary configurations steps required before installing Adobe Campaign.

The technical and software configuration required for installing Adobe Campaign is detailed in the [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

As a reminder, the following components need to be installed and correctly configured:

* Apache, refer to [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html),
* Java JDK and OpenJDK, refer to [Java Development Kit - JDK](https://helpx.adobe.com/campaign/standard/installation/using/application-server.html#java-development-kit---jdk),
* Libraries, refer to [Libraries](https://helpx.adobe.com/campaign/standard/installation/using/prerequisites-of-campaign-installation-in-linux.html#libraries),
* Database access layers, refer to [Database access layers](https://helpx.adobe.com/campaign/standard/installation/using/prerequisites-of-campaign-installation-in-linux.html#database-access-layers),
* LibreOffice, refer to [Installing LibreOffice for Debian](https://helpx.adobe.com/campaign/standard/installation/using/prerequisites-of-campaign-installation-in-linux.html#installing-libreoffice-for-debian) and [Installing LibreOffice for CentOS](https://helpx.adobe.com/campaign/standard/installation/using/prerequisites-of-campaign-installation-in-linux.html#installing-libreoffice-for-centos),
* Fonts, refer to [Fonts for MTA statistics](https://helpx.adobe.com/campaign/standard/installation/using/prerequisites-of-campaign-installation-in-linux.html#fonts-for-mta-statistics) and [Fonts for Japanese instances](https://helpx.adobe.com/campaign/standard/installation/using/prerequisites-of-campaign-installation-in-linux.html#fonts-for-japanese-instances).

>[!NOTE]
>
>To install a build lower or equal to 8709 on CentOS 7 and Debian 8 platforms the apache access_compat module must be enabled.

### Libraries {#libraries}

To install Adobe Campaign in Linux, please make sure you have the required libraries.

* Library C must be able to support TLS (Thread Local Storage) mode. This mode is active in most cases except with some kernels for which Xen support has been disabled.

  To check this, you can use the **uname -a | grep xen** command for example.

  If the command doesn't return anything (empty line), it means configuration is correct.

* You must have **version 0.9.8** or **1.0** of OpenSSL.

  For RHEL and CentOS 6 distributions, version 1.0 of OpenSSL is required.

* To use Adobe Campaign, you need to have the **libicu** library installed.

  >[!NOTE]
  >
  >RHEL 7 distribution is provided with the **libicu5.0** library

  The following versions of **libicu** are supported (32bit or 64bit):

    * RHEL, SLES, CentOS : **libicu4.2**. 
    * Debian 7: **libicu4.8**, Debian 8: **libicu5.2**.

  The **libc-ares2** is provided out-of-the-box with Adobe Campaign for RHEL or CentOS installations.

  If installing in Debian, you must run the following command to install the library:

  ```
  aptitude install libc-ares2
  ```

### SELinux {#selinux}

When used, the SELinux module must be properly configured.

To do this, log on as root and enter the following command:

```
echo 0 >/selinux/enforce
```

In addition to this, in the **/etc/sysconfig/httpd** file, the following line was added to reference the Adobe Campaign environment configuration script:

```
. ~neolane/nl6/env.sh
```

In RHEL and CentOS, compatibility issues with the client layers of databases were noted when SELinux is enabled. To be sure Adobe Campaign is able to operate correctly, we recommend disabling SELinux.

Apply the following process:

Edit the file **/etc/selinux/config**

Modify the SELINUX line as follows:

```
SELINUX=disabled
```

### Fonts for MTA statistics {#fonts-for-mta-statistics}

In order for reports on MTA statistics (nms/fra/jsp/stat.jsp) to be displayed correctly, add fonts.

In Debian, add the command:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

In Redhat, use the following command:

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Fonts for Japanese instances {#fonts-for-japanese-instances}

Fonts of specific characters are necessary for the Japanese instances in order to export the reports to PDF format.

In Debian, add the command:

```
aptitude install fonts-ipafont
```

In Red Hat, add the command:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Installing LibreOffice for Debian {#installing-libreoffice-for-debian}

For Debian, the following configurations are required:

1. Install the following standard packages:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Install the following fonts (optional but highly recommended for Japanese instances):

   ```
   apt-get install fonts-ipafont
   ```

### Installing LibreOffice for CentOS {#installing-libreoffice-for-centos}

The following configurations are necessary with CentOS:

1. Install the following standard packages:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Install the following fonts (optionnal but highly recommended for Japanese instances):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Database access layers {#database-access-layers}

The access layers for the database engine you are using must be installed on your server and be accessible via the Adobe Campaign account. Versions and installation modes may vary depending on the database engine used.

The supported pilot version are detailed in the [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Also check the general [Database](https://helpx.adobe.com/campaign/standard/installation/using/database.html) section.

### PostgreSQL {#postgresql}

Adobe Campaign supports all versions of the PostgreSQL client libraries from version 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** and **libpq.so.3.1**).

Using PostgreSQL with Adobe Campaign also requires installing the corresponding **pgcrypto** libraries.

### Oracle {#oracle}

Retrieve the library version for 64-bit Debian, i.e.: **libclntsh.so**, **libclntsh.so.11.1** and **libclntsh.so.10.1**.

You can obtain a Linux RPM package from the Oracle Technology Network.

>[!NOTE]
>
>If you have already installed the Oracle client but the global environment (for instance: /etc/profile) isn't properly configured, you can add missing information to the **nl6/customer.sh** script For more on this, refer to [Environment variables](https://helpx.adobe.com/campaign/standard/installation/using/installing-packages-with-linux.html#environment-variables).

**Troubleshooting and best practices**

Problems can appear after an Oracle client or a server update, change of version or at the first installation of the instance.

If you notice on the client console that there are unexpected time lags (one or more hours) in logs, workflow last processing, next processing, and so on, there might be a problem between the library of the Oracle client and the Oracle Server. To avoid such problems

1. Make sure to use the **full client**

   Various problems have been identified when using the Oracle Instant Client version. In addition, it is impossible to change the Timezone file on instant client.

1. Make sure that the **client version** and the **database server version** are the **same**.

   Mixing versions despite Oracle's compatibility matrix and recommendation to align client and server versions is known to cause problems.

   Also check ORACLE_HOME value to make sure it points to the expected client version (in case several versions are installed on the machine).

1. Make sure the client and the server use the same **timezone file**.

### DB2 {#db2}

The library version supported is **libdb2.so**.

## Implementation steps {#implementation-steps}

Adobe Campaign installations for Linux must be carried out in the following sequence: server installation followed by instance configuration.

The installation process is described in this chapter. The installation steps are as follows:

* Step 1: Installing the application server, refer to [Installing packages with Linux](https://helpx.adobe.com/campaign/standard/installation/using/installing-packages-with-linux.html).
* Step 2: Integrating with a Web server (optional, depending on the components deployed).

Once the installation steps are complete, you need to configure the instances, the database and the server. For more on this, refer to [About initial configuration](https://helpx.adobe.com/campaign/standard/installation/using/about-initial-configuration.html).
