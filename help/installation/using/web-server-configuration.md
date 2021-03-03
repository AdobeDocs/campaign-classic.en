---
solution: Campaign Classic
product: campaign
title: Web-server configuration
description: xxxx
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
---

# Web-server configuration {#web-server-configuration}

You will find below some of the main best practices related to web-server Apache/IIS) configuration.

Change default error pages.

Disable old SSL version and ciphers:

on Apache, edit /etc/apache2/mods-available/ssl.conf. Here is an example:
SSLProtocol all -SSLv2 -SSLv3 -TLSv1
SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1
on IIS (see the documentation), perform the following configuration:
Add registry subkey in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
To enable the system to use the protocols that will not be negotiated by default (such as TLS 1.2), change the DWORD value data of the DisabledByDefault value to 0x0 in the following registry keys under the Protocols key:

SCHANNEL\Protocols\TLS 1.2\Client

SCHANNEL\Protocols\TLS 1.2\Server

Disable SSL x.0:

SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32-bit) Value to 1

SCHANNEL\Protocols\SSL 3.0\Server: Enabled: DWORD (32-bit) Value to 0

Remove the TRACE method:

on Apache, edit in /etc/apache2/conf.d/security: TraceEnable Off
on IIS (see the documentation), perform the following configuration:
Make sure that Request Filtering role service or feature is installed.
In the Request Filtering pane, click the HTTP verbs tab, and then click Deny Verb. In the Actions pane, enter TRACE in the open dialog.
Remove the banner:

on Apache, edit /etc/apache2/conf.d/security:
ServerSignature Off
ServerTokens Prod
on IIS (see the documentation), perform the following configuration:
Install URLScan.
Edit the Urlscan.ini file to have RemoveServerHeader=1
Limit query size to prevent important files from being uploaded:

On Apache (see the documentation), add the LimitRequestBody directive (size in bytes) in / directory.

<Directory />
        Options FollowSymLinks
        AllowOverride None
        LimitRequestBody 10485760
</Directory>
On IIS (see the documentation), set the maxAllowedContentLength (maximum allowed content length) in the content filtering options.
