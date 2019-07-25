---
title: Client console availability for Windows
seo-title: Client console availability for Windows
description: Client console availability for Windows
seo-description: 
page-status-flag: never-activated
uuid: 9825f074-3c5c-409e-9823-e9daec562ac1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 29fae61c-72ef-486d-b46c-156bbd9d0540
index: y
internal: n
snippet: y
---

# Client console availability for Windows{#client-console-availability-for-windows}

For Adobe Campaign users to be able to log on to the instance you have created and configured, they need to use the client console.

When the computer used to start an Adobe Campaign application server (**nlserver web**) receives user connections from the client console, you can configure it to make the setup program for the Adobe Campaign rich client available via an HTML interface.

To do this, you must:

1. Recover the package that contains the console installation program.

   This file is called **setup-client-7.**X**.**XXXX**.exe** for v7 or **setup-client-6.**X**.**XXXX**.exe** for v6.1, where 'X' is the sub-version of Adobe Campaign and **XXXX** is the build number.

1. Copy and paste this package into the Adobe Campaign installation folder, under **/datakit/nl/eng/jsp**.
1. Start the Adobe Campaign server.

The final users may then download the console installation program via a Web browser thanks to the following URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

This page requires a login and password defined in the application.

To download and install the console, refer to [Installing the client console](../../installation/using/installing-the-client-console.md).

Whenever a new version of the client console is available, you are invited to download it.

>[!NOTE]
>
>In the prompt that is displayed, Adobe recommends leaving the option **No longer ask this question** unselected to make sure that all users are alerted when a new version of the console is available.  
>If you select this option and choose not to download the latest version, no other user will be informed of new available versions.

To reset this prompt, follow the steps below (only system administrators comfortable with editing the Registry should make these changes):

1. Open Registry Editor using the **regedit** command from the **Start > Run** menu.
1. Search for the node and expand it.

   ```
   \HKEY_CURRENT_USERSoftwareNeolaneNL_6nlclient
   ```

1. Delete the **confAdvisedUpgrade** entry and close Registry Editor.

