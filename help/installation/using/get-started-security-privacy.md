---
solution: Campaign Classic
product: campaign
title: Get started with security and privacy
description: Learn more about the key elements to check regarding security and privacy.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
---
# Get started with security and privacy {#get-started-security-privacy}

This section will introduce you to the key elements to check regarding security and privacy. Some configurations can only be performed by on-premise customers.

## Privacy

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

Privacy configuration and hardening is a key element of security optimization. Here are some best practices to follow regarding privacy:

* Protect your customer PII by using HTTPS instead of HTTP
* Use PII view restriction to protect privacy and prevent data from being misused.
* Make sure that encrypted passwords are restricted.
* Protect the pages that might contain personal information such as mirror pages, web applications, etc.

[Read more](../../installation/using/privacy.md)

## Access management

<img src="assets/do-not-localize/icon_access.svg" width="60px">

Access management is an important part of security hardening. Here are some of the main best practices:

* Create enough security groups
* Check that each operator has the appropriate access rights
* Avoid using the admin operator and avoid having too many operators in the admin group

[Read more](../../installation/using/access-management.md)

## Scripting and coding guidelines

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

When developing in Adobe Campaign (workflows, Javascript, JSSP, etc.), always follow these guidelines:

* **Scripting**: try to avoid SQL statements, use parameterized functions instead of string concatenation, avoid SQL injection by adding the SQL functions to use to the allow list.

* **Secure the data model**: use named rights to limit operator actions, add system filters (sysFilter)

* **Add captchas in web applications**: learn how to add captchas in your public landing pages and subscription pages.

[Read more](../../installation/using/scripting-coding-guidelines.md)

## Network, database and SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

A very important thing to check when deploying an on-premise type of architecture is the networking configuration. 

It is also imperative that you follow your database engine security.

[Read more](../../installation/using/network-database.md)

## Server configuration

<img src="assets/do-not-localize/icon_server.svg" width="60px">

Configuration has to be performed on all servers. The configuration files are of the type **serverConf.xml** and **`config-<instance>.xml`**. Here are the key elements that need to be verified:

* **Security zones**: Configure security zones so that they directly take into account the IP addresses of clients of a proxy.

* **File upload protection**: limit the types of files that can be uploaded to the Adobe Campaign server using a new uploadAllowList attribute. This can be used in the server configuration file.

* **Relay**: fine tune the relay configuration by deactivating the relay rules for unused modules/applications.

* **Outgoing connection protection** and **Command restriction** (server-side)

* You can also add extra HTTP headers, activate checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Refer to the [Campaign server configuration documentation](../../installation/using/configuring-campaign-server.md) and the [Server configuration file description](../../installation/using/the-server-configuration-file.md) for more information.

[Read more](../../installation/using/server-configuration.md)

## Web-server configuration

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Several best practices should be followed when configuring your web-server (Apache/IIS):

* Disable old SSL version and ciphers
* Remove the TRACE method
* Remove the banner
* Limit query size to prevent important files from being uploaded

[Read more](../../installation/using/web-server-configuration.md)
