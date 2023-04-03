---
product: campaign
title: Technote - Enabling Microsoft Edge Chromium on your Campaign environment
description: Campaign - Edge Chromium
hide: yes
hidefromtoc: yes
---

# How to enable Microsoft Edge Chromium on your environment {#edge-conf}

![](../../assets/v7-only.svg)


## What changed?

Following the end of life of Microsoft Internet Explorer 11, the HTML rendering engine for dashboards in the client console is using Edge Chromium, starting Campaign Classic v7.3.

In addition to the installation of Microsoft Edge Webview 2 runtime, which is now [required for any client console installation](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium must be enabled on your instance(s). 

## Are you impacted?

If your environment has been upgraded to Campaign Classic v7.3 (or later), you are impacted.

## How to update?

* As a **hosted** customer, Adobe already enabled Microsoft Edge Chromium on your instance(s). No additional action is required.

* As an **on-premise/hybrid** customer, you need to enable Microsoft Edge Chromium on your instance(s). 
    
    When upgrading to Campaign Classic v7.3 (and later), a new `webView2Mode` attribute is available in the Campaign server configuration file `serverConf.xml`. This attribute must be enabled.

    To perform this, apply the following steps on all your environments (MKT, MID, RT):

    1. Edit the Campaign server configuration file (`serverConf.xml`)
    1. In the `<web>` module, set `webView2Mode = "1"`
    1. Reload the server configuration 

        ```
        nlserver config -reload
        ```

    1. Restart the web server

        ```
        nlserver restart web
        ```

    1. If your environment runs on Apache, restart Apache

        ```
        /etc/init.d/apache2 restart
        ```


>[!NOTE]
>
>For any questions about these changes, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Related topics

* [Upgrade your environment](../../production/using/build-upgrade.md)
* [Build upgrade FAQ](../../platform/using/faq-build-upgrade.md)
* [Install Campaign Client Console](../../installation/using/installing-the-client-console.md)

