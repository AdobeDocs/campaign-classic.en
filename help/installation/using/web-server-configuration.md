---
product: campaign
title: Web-server configuration
description: Learn more about web-server configuration main best practices
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
TQID: https://experienceleague.adobe.com/ylf7sIKiO9ip-yC3M4zqbhu0ITaXqmTMQJ-4KfNQlt8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
    internal-label: Governance
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Web-server configuration {#web-server-configuration}



You will find below some of the main best practices related to web-server (Apache/IIS) configuration.

* Change default error pages.

* Disable old SSL version and ciphers:

   **On Apache**, edit /etc/apache2/mods-available/ssl.conf. Here is an example:

    * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
    * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

    **On IIS** (see the [documentation](https://support.microsoft.com/en-us/kb/245030)), perform the following configuration:

    * Add registry subkey in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
    * To enable the system to use the protocols that will not be negotiated by default (such as TLS 1.2), change the DWORD value data of the DisabledByDefault value to 0x0 in the following registry keys under the **Protocols** key:

        SCHANNEL\Protocols\TLS 1.2\Client

        SCHANNEL\Protocols\TLS 1.2\Server

    **Disable SSL x.0**

    SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32-bit) Value to 1

    SCHANNEL\Protocols\SSL 3.0\Server: Enabled: DWORD (32-bit) Value to 0

* Remove the **TRACE** method:

    **On Apache**, edit in /etc/apache2/conf.d/security: TraceEnable **Off**

    **On IIS** (see the [documentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), perform the following configuration:

    * Make sure that **Request Filtering** role service or feature is installed.
    * In the **Request Filtering** pane, click the HTTP verbs tab, and then click Deny Verb. In the Actions pane, enter TRACE in the open dialog.

* Remove the banner:

    **On Apache**, edit /etc/apache2/conf.d/security:
    
    * ServerSignature **Off**
    * ServerTokens **Prod**

    **On IIS**, perform the following configuration:

    * Install **URLScan**.
    * Edit the **Urlscan.ini** file to have **RemoveServerHeader=1**

* Limit query size to prevent important files from being uploaded:

    **On Apache**, add the **LimitRequestBody** directive (size in bytes) in / directory.

    ```
    <Directory />
        Options FollowSymLinks
        AllowOverride None
        LimitRequestBody 10485760
    </Directory>
    ```

    **On IIS** (see the [documentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), set the **maxAllowedContentLength** (maximum allowed content length) in the content filtering options.

Related topics:

* [Adobe Marketing Cloud Compliance overview](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign Security overview](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#security)
