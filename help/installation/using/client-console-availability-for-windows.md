---
product: campaign
title: Client console availability for Windows
description: Client console availability for Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
---
# Client console availability for Windows{#client-console-availability-for-windows}

![](../../assets/v7-only.svg)

For Adobe Campaign users to be able to log on to the instance you have created and configured, they need to use the client console.

## Make the client console available

When the computer used to start an Adobe Campaign application server (**nlserver web**) receives user connections from the client console, you can configure it to make the setup program for the Adobe Campaign rich client available via an HTML interface. Whenever a new version of the client console is available, users are invited to download it when launching their client console.

To do this, you must:

1. Select the package that contains the console installation program.

   This file is called `setup-client-7.X.XXXX.exe` for v7 or `setup-client-6.X.XXXX.exe` for v6.1, where `X` is the sub-version of Adobe Campaign and `XXXX` is the build number.

1. Copy and paste this package into the Adobe Campaign installation folder (on the marketing server for hybrid installations), under **/datakit/nl/eng/jsp**.
1. Start Adobe Campaign server.

Campaign users can then download the console installation program via a web browser thanks to the following URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

This page requires a login and password defined in the application.

Learn how to install the console [in this section](../../installation/using/installing-the-client-console.md).

## Propose end users to upgrade their client console

Once the console is available in Campaign server folder, users are invited to download the latest client console version in a dedicated the prompt window. Adobe recommends leaving the option **[!UICONTROL No longer ask this question]** unselected to make sure that all users are alerted when a new version of the console is available.  

If you select this option and choose not to download the latest version, no other user will be informed of new available versions.

In case the option was selected, you can reset this prompt. Only system administrators comfortable with editing Windows Registry should make these changes:

1. Open Registry Editor using the **regedit** command from the **[!UICONTROL Start > Run]** menu.
1. Search for the node and expand it.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Delete the **confAdvisedUpgrade** entry and close Registry Editor.
