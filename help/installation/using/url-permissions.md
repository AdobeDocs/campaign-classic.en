---
solution: Campaign Classic
product: campaign
title: Configure URL permissions
description: Learn how to configure URL permissions
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814,6fe8da3b-57b9-4a69-8602-a03993630b27
---
# Configure URL permissions (on-premise){#url-permissions}

The default list of URLs that can be called by JavaScript codes (workflows, etc.) by your Campaign Classic instances is limited. These are URLs that allow your instances to function properly.

By default, instances are not allowed to connect to outside URLs. However, it is possible to add some outside URLs to the list of authorized URLs, so that your instance can connect to them. This allows you to connect your Campaign instances to outside systems like, for example, SFTP servers or websites in order to enable file and/or data transfer.

>[!NOTE]
>
>This procedure is restricted to **on-premise** deployments. 
>
>As a **hosted** customer, if you can access [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html), you can use the URL permissions self service interface. [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html)
>
>Other **hybrid/hosted** customers need to reach out to Adobe support team to add IP to the allow list.
>

For **Hybrid** and **On-premise** deployments, the administrator needs to reference a new **urlPermission** in the **serverConf.xml** file.


Three connection protection modes are available:

* **Blocking**: all URLs that do not belong to the allowlist are blocked, with an error message. This is the default mode after a postupgrade.
* **Permissive**: all URLs that do not belong to the allowlist are allowed.
* **Warning**: all URLs that do not belong to the allowlist are allowed, but the JS interpreter emits a warning, so that the administrator can collect them. This mode adds JST-310027 warning messages.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>By default, new implementations use the **Blocking** mode. 
>
>As an existing customer coming from a migration, you can temporary use the **Warning** mode. Analyze the outbound traffic before allowing the URLs. Once the list of allowed URLs defined, you can add the URLs to the allowlist and activate the **Blocking** mode.

For more information, refer to these sections:

* [Control Panel documentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Hosting models](hosting-models.md)
* [Campaign server configuration](configuring-campaign-server.md)
* [Campaign server configuration file parameters](the-server-configuration-file.md)
* [Security and Privacy checklist](get-started-security-privacy.md)
