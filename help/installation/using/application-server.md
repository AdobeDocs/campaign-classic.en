---
product: campaign
title: Application server
description: Application server
feature: Installation
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
---
# Application server{#application-server}

The required database access layers must be installed on the server and accessible from the Adobe Campaign account.

## Java Development Kit - JDK {#jdk}

Java Development Kit, or JDK, is a software development kit. It is the foundational component that enables Java application and Java applet development. 

The dynamic Web page generator uses JSP technology. For this, a Tomcat engine (from Apache) is included in the application. It requires a Java Development Kit (JDK), installed on all servers which the Adobe Campaign application is installed on.

You must first install a JDK on the computers on which you wish to run the Adobe Campaign application server (**nlserver web** process) because it incorporates a servlet container, Apache Tomcat, used to generate dynamic Web pages (reports, Web forms, etc).

The application has been approved for the Java Development Kit (JDK) developed by Oracle as well as for **OpenJDK**.

The supported versions are detailed in Campaign [Compatibility matrix](../../rn/using/compatibility-matrix.md).


>[!AVAILABILITY]
>
>* Starting v7.4.1, Campaign requires at least **Java JDK 11**. If your Campaign server is installed in a Windows environment, the Java Runtime (JRE) is no longer detected automatically. The JRE_HOME environment variable must be set to the folder where Campaign can locate the `bin/server/jvm.dll` file. For example, if your JDK 11 is installed under the `C:\Program Files\Java\jdk-11` folder, your JRE_HOME must be `C:\Program Files\Java\jdk-11`.
>
>* Starting v7.4.1, Tomcat 10.1 is the default version.
>

### Recommendations

When installing and upgrading your Java Development Kit, apply the following recommendations:

* Java Development Kit can be installed using the appropriate JDK version already used by other applications on the machine.

* When installing the JDK, the integration with the Web browsers is not required.  

* On a machine which only executes delivery agents (**nlserver mta** process) or the workflow server (**nlserver wfserver** process), installing a JDK is not required.

* When upgrading your Java version, you first need to uninstall the previous version. Both versions of Java installed in the same machine can cause conflicts.
    
    As an On-premise customer, you can check the `LD_LIBRARY_PATH` [environment variable](installing-packages-with-linux.md#environment-variables) is set to the latest version (for ex. java11). If it is set to a previous version (for ex. Java8), then it needs to be updated. For JDK 11, the path to locate JDK libraries is `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Installation steps

Java Development Kit is platform-specific: separate installers are needed for each operating system.

To download JDK, connect to [Oracle website](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Make sure to download a Java Development Kit (JDK), not a Java Runtime Environment (JRE).


To install the JDSL in a Linux environment, Adobe recommends to use a package manager.

For Debian, use the following command:

```sql
apt install openjdk-11-jdk-headless
```

For RHEL, use the following command:

```sql
dnf install java-11-openjdk-headless
```

## Export reports {#exporting-reports}

You can use Adobe Campaign to export reports into Microsoft Excel and Adobe PDF. 

* For the Microsoft Excel format, Adobe Campaign relies on **LibreOffice**. 

* For the Adobe PDF format, Adobe Campaign uses the **PhantomJS** converter. PhantomJs is included in the factory package and LibreOffice must be installed on the machine(s) which the Adobe Campaign application server is executed on (**nlserver web** process).

>[!NOTE]
>
>For Linux, you will need to add fonts. For more on this, refer to [Fonts for MTA statistics](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin lets you assign a score to emails in order to determine whether a message risks to be considered as undesirable by anti-spam tools used on reception. Installation is optional.

The qualification of emails as undesirable by SpamAssassin is based entirely on filtering and scoring rules. These rules therefore have to be updated at least once a day in order for your SpamAssassin installation and its integration into Adobe Campaign to be fully functional and to guarantee the relevance of scores assigned to your deliveries before sending. This update is the responsibility of the server administrator hosting SpamAssassin.

The minimum supported version is: **3.4**

SpamAssassin requires a HTTP internet access (tcp/80).

Installation and configuration stages for SpamAssassin are presented in [Configuring SpamAssassin](../../installation/using/configuring-spamassassin.md).
