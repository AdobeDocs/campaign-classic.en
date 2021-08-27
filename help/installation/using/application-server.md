---
product: campaign
title: Application server
description: Application server
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
---
# Application server{#application-server}

![](../../assets/v7-only.svg)

The required database access layers must be installed on the server and accessible from the Adobe Campaign account.

## Java Development Kit - JDK {#java-development-kit---jdk}

The dynamic Web page generator uses JSP 1.2 technology. For this, a Tomcat engine (from Apache) is included in the application. It requires a Java Development Kit (JDK), installed on all servers which the Adobe Campaign application is installed on.

You must first install a JDK on the computers on which you wish to run the Adobe Campaign application server (**nlserver web** process) because it incorporates a servlet container, Apache Tomcat, used to generate dynamic Web pages (reports, Web forms, etc).

The application has been approved for the Java Development Kit (JDK) developed by Oracle as well as for **OpenJDK**.

The supported versions are detailed in Campaign [Compatibility matrix](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>It can be installed using the appropriate JDK version already used by other applications on the machine.
>  
>When installing, you are not required to perform the integration with the Web browsers.  
>
>On a machine which only executes delivery agents (**nlserver mta** process) or the workflow server (**nlserver wfserver** process), installing a JDK isn't necessary.

To download Java JDK, connect to: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html). 

**Warning: you must download a JDK, not a JRE.**

>[!CAUTION]
>
>To preserve platform operation performance and ensure compatibility with the installed version, you must disable automatic JDK update functions in Windows and Linux.

To install the JDSL in a Linux environment, it is preferable to use a package manager.

In Debian 8 and 9, use the following command:

```
aptitude install openjdk-8-jdk
```

For RHEL 7, use the following command:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

In Linux, OpenSSL must be installed. The versions supported by Adobe Campaign are **OpenSSL 1.0.1** and **OpenSSL 0.9.8**. Sub-versions 0.9.8g to 0.9.8o are accepted.

## Exporting reports {#exporting-reports}

Adobe Campaign lets you export platform reports in Microsoft Excel and Adobe PDF format. For the Microsoft Excel format, Adobe Campaign uses **LibreOffice**. For the Adobe PDF format, Adobe Campaign uses the **PhantomJS** converter. PhantomJs is included in the factory package and LibreOffice must be installed on the machine(s) which the Adobe Campaign application server is executed on (**nlserver web** process).

>[!NOTE]
>
>For Linux, you will need to add fonts. For more on this, refer to [Fonts for MTA statistics](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin lets you assign a score to emails in order to determine whether a message risks to be considered as undesirable by anti-spam tools used on reception. Installation is optional.

The qualification of emails as undesirable by SpamAssassin is based entirely on filtering and scoring rules. These rules therefore have to be updated at least once a day in order for your SpamAssassin installation and its integration into Adobe Campaign to be fully functional and to guarantee the relevance of scores assigned to your deliveries before sending. This update is the responsibility of the server administrator hosting SpamAssassin.

The minimum supported version is: **3.4**

SpamAssassin requires a HTTP internet access (tcp/80).

Installation and configuration stages for SpamAssassin are presented in [Configuring SpamAssassin](../../installation/using/configuring-spamassassin.md).
