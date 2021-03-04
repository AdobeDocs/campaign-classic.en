---
solution: Campaign Classic
product: campaign
title: Locate Tomcat version in Adobe Campaign
description: Learn how to find out the current version of embedded Tomcat web servlet used in an instance of Adobe Campaign.
audience: production
content-type: reference
topic-tags: troubleshooting
---

# Locating Tomcat version{#locate-tomcat-version}

Adobe Campaign uses an **embedded web servlet called Apache Tomcat** to process HTTP/HTTPS requests between the application and any external interface (including Client Console, tracked URL links, SOAP calls, and others). There is often an external web server (usually IIS or Apache) in front of this for any external-facing Adobe Campaign instances.

Follow the procedure below to find out the exact version of Tomcat used in a **Campaign Classic on-premise instance** in order to help troubleshoot issues.

## Tomcat used in Adobe Campaign

Tomcat runs on Java and requires JDK to be installed. For more information, see Java Development Kit (JDK) in the [Campaign Compatibility Matrix](../../rn/using/compatibility-matrix.md) section.

The Tomcat used in Adobe Campaign is a customized embedded version that does not use all the features of the full generally available release of Tomcat, and may not suffer all the vulnerabilities of the full version. The Tomcat should also not be exposed to the outside internet, and any Adobe Campaign instances which are exposed should have an external web server (IIS, Apache, etc.) in front of the Tomcat to protect it.

New or upgraded versions of the embedded versions of Tomcat are only released with new builds of Adobe Campaign itself and not as separate patches outside of the Adobe Campaign builds.

## How to locate the version of embedded Tomcat

To locate the version of embedded Tomcat in an instance of Adobe Campaign, follow the steps below.

>[!NOTE]
>
>You must have access to the files on the Adobe Campaign server you need to check. The procedure described below only applies to **on-premise hosting models**.

1. Navigate to the *\tomcat-7\lib* subfolder within the Adobe Campaign installation folder (for example, *C:\Program Files\ [Installation_folder]* in Windows, or */usr/local/neolane/nl6* in Linux).

    If you are running an older version of Adobe Campaign using Tomcat v6, use *\tomcat-6\lib*.

1. Copy the file *catalina.jar* to an outside temporary folder (for example, your desktop) and rename the extension from .jar to .zip.

1. Unzip the copied file. It will result in many subfolders and files.

1. Within the unzipped files/folders, open or read the following contained file using a text editor: *org/apache/catalina/util/ServerInfo.properties*. You may need to add a .txt extension to facilitate opening with a text editor.

1. Once finished, if it is on a server machine, delete the temporary file(s) you created.

As an example, the *ServerInfo.properties* file for Adobe Campaign will contain the following information, indicating Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

Once you are able to establish the exact version of Tomcat used in a particular instance, it may help you in troubleshooting Tomcat-related issues.

>[!NOTE]
>
>The major version of the embedded Tomcat is only upgraded when the major version of Adobe Campaign changes (although older versions may no longer be officially supported, the information may be useful as some customers may still be running these versions).
>
>For example, Adobe Campaign v6.02 will always use Tomcat v6.x.