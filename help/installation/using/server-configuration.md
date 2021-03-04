---
solution: Campaign Classic
product: campaign
title: Server configuration
description: xxxx
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
---

# Server configuration {#server-configuration}

Configuration has to be performed on all servers. The configuration files are of the type **serverConf.xml** and **`config-<instance>.xml`**. Here are the key elements that need to be verified:

* **Security zones**: Configure security zones so that they directly take into account the IP addresses of clients of a proxy.

* **File upload protection**: limit the types of files that can be uploaded to the Adobe Campaign server using a new uploadAllowList attribute. This can be used in the server configuration file.

* **Relay**: fine tune the relay configuration by deactivating the relay rules for unused modules/applications.

* **Outgoing connection protection** and **Command restriction** (server-side)

* You can also add extra HTTP headers, activate checkIPConsistent, enableTLS, sessionTimeOutSec, etc.
Refer to the [Campaign server configuration documentation](../../installation/using/configuring-campaign-server.md) and the [Server configuration file description](../../installation/using/the-server-configuration-file.md) for more information.

## Configuring security zones

>[!IMPORTANT]
>
>From build 8977 onwards, the Security Zones Self Service User Interface is not available anymore.
>
>* If you are hosted on AWS, adding IP to the allow list must be performed in Control Panel. For more information, refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).
>* If you are not hosted on AWS, reach out to Adobe support team to add IP to the allow list.
>
>To check if your instance is hosted on AWS, follow the steps detailed in [this section](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

To learn how to use the Security Zones Self Service UI to manage entries in the VPN Security Zone configuration, refer to [this technote](https://helpx.adobe.com/campaign/kb/configuring-security-zones-self-service.html).

Make sure that your reverse proxy in not allowed in subNetwork. If it is the case, **all** traffic will be detected as coming from this local IP, so will be trusted.

Minimize the use of **sessionTokenOnly="true"**:

>[!IMPORTANT]
>
>If this attribute is set to true, the operator can be exposed to a **CRSF attack**.

* In addition, the sessionToken cookie is not set with an httpOnly flag, so some client-side javascript code can read it.
* However Message Center on multiple execution cells needs sessionTokenOnly: create a new security zone with sessionTokenOnly set to "true" and add **only the needed IP(s)** in this zone.

When possible, set all allowHTTP, showErrors to be false (not for localhost) and **check them.**

* allowHTTP = "false": forces operators to use HTTPS
* showErrors = "false": hides technical errors (including SQL ones). It prevents displaying too much information, but reduces the capability for the marketer to solve mistakes (without asking for more information from an administrator)

Set allowDebug to **true** only on IPs used by marketing users/administrators who need to create (in fact preview) surveys, webApps and reports. This flag allows these IPs to get relay rules displayed and to debug them.

**Never set allowEmptyPassword, allowUserPassword, allowSQLInjection to true**. These attributes are only here to allow a smooth migration from v5 and v6.0:

* **allowEmptyPassword** lets operators have an empty password. If this is the case for you, notify all your operators to ask them to set a password with a deadline. Once this deadline has passed, change this attribute to false.

* **allowUserPassword** lets operators send their credentials as parameters (so they will be logged by apache/IIS/proxy). This feature was used in the past to simplify API usage. You can check in your cookbook (or in the specification) whether some third-party applications use this. If so, you have to notify them to change the way they use our API and as soon as possible remove this feature.

* **allowSQLInjection** lets the user perform SQL injections by using an old syntax. As soon as possible carry out the corrections described in [this page](../../migration/using/general-configurations.md) to be able to set this attribute to false.
You can use /nl/jsp/ping.jsp?zones=true to check your security zone configuration. This page displays the active status of security measures (computed with these security flags) for the current IP.

HttpOnly cookie/useSecurityToken: refer to **sessionTokenOnly** flag.

Minimize IPs added to the allow list: Out of the box, in security zones, we have added the 3 ranges for private networks. It is unlikely that you will use all of these IP addresses. So keep only the ones that you need.

Update webApp/internal operator to be only accessible in localhost.

## File upload protection

Check with operational users what kind of files they upload to the server using nlclient/web interface. As a reminder, business needs can be:

* images (jpg, gif, png, ...)
* content (zip, html, css, ...)
* marketing assets (doc, xls, pdf, psd, tiff, ...)
* email attachment (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* etc.

Add all of them in serverConf/shared/datastore/@uploadAllowlist (valid java regular expression). Learn more in [this page](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

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

By default, Adobe Campaign's MTA does not use a secured connection to send content to the SMTP server. You have to enable this feature (may reduce delivery speed). To do this, set enableTLS to tr**ue in the `<smtp ...>` node.

You can reduce the lifetime of a session in the authentication node (sessionTimeOutSec attribute).
