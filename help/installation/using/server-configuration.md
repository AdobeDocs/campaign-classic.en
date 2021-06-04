---
product: campaign
title: Server security configuration
description: Learn more about server configuration best practices
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
---
# Server security settings {#server-configuration}

## File upload protection

Check with operational users what kind of files they upload to the server using Campaign Client Console or web interface. As a reminder, business needs can be:

* images (jpg, gif, png, ...)
* content (zip, html, css, ...)
* marketing assets (doc, xls, pdf, psd, tiff, ...)
* email attachment (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* etc.

Add all of them in serverConf/shared/datastore/@uploadAllowlist (valid java regular expression). Learn more in [this page](../../installation/using/file-res-management.md).

Adobe Campaign does not restrict the file size. But you can do it by configuring IIS/Apache. Learn more in [this section](../../installation/using/web-server-configuration.md).

## Relay

Please refer to [this page](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) for more information.

By default, all dynamic pages are automatically relayed to the local Tomcat server of the machine whose Web module is started. You can choose to not relay some of them. If you are not using some Adobe Campaign modules (such as webapp, interaction, some jsp) you can remove them from relay rules.

Out of the box, we have forced the capability to display end user resources using http (httpAllowed="true"). As these pages can display some PII (such as email content, address), redeem coupon, offer, you should force HTTPS again on these paths.

If you are using different host names (one public and one for operators), you can also prevent the relaying of some resources needed by operators over the public DNS name.

## Outgoing connection protection

The default list of URLs that can be called by JavaScript codes (workflows, etc.) is limited. To allow a new URL, the administrator needs to reference it in the [serverConf.xml file](../../installation/using/the-server-configuration-file.md).

Three connection protection modes exist:

* **Blocking** : all URLs that do not belong to the allow list are blocked, with an error message. This is the default mode after a postupgrade.
* **Permissive** : all URLs that do not belong to the allow list are allowed.
* **Warning** : all URLs not on the allow list are allowed, but the JS interpreter emits a warning, so that the administrator can collect them. This mode adds JST-310027 warning messages.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

New clients will use the blocking mode. If they want to allow a new URL, they need to contact their administrator to add it to the allow list.

Existing customers coming from a migration can use the warning mode for a while. Meanwhile they need to analyze the outbound trafic before authorizing the URLS.

## Command restriction (server-side)

Several commands are blacklisted and cannot be executed using the execCommand function. An extra-security is provided by a dedicated Unix user to execute external commands. For hosted installations, this restriction is automatically applied. For on-premise installations, you can manually set up this restriction by following the instructions from [this page](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). In addition, **[!UICONTROL Script]** and **[!UICONTROL External task]** workflow activities are not available (newly installed instances).

## Other configurations

You can add extra HTTP headers for all pages (for more information, refer to [this page](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* You can add some additional headers such as HSTS, X-FRAME-OPTIONS, CSP...
* You have to test them in a test environment before applying them in production. 
    
    >[!IMPORTANT]
    >
    >Adobe Campaign can be broken by adding certain headers.

Adobe Campaign lets you set a plain password in the `<dbcnx .../>` element. Do not use this feature.

By default, Adobe Campaign does not stick a session to a specific IP, but you can active it to prevent the session from being stolen. To do it, in the [serverConf.xml file](../../installation/using/the-server-configuration-file.md), set the checkIPConsistent attribute to **true** in the `<authentication>` node.

By default, Adobe Campaign's MTA does not use a secured connection to send content to the SMTP server. You have to enable this feature (may reduce delivery speed). To do this, set **enableTLS** to **true** in the `<smtp ...>` node.

You can reduce the lifetime of a session in the authentication node (sessionTimeOutSec attribute).
