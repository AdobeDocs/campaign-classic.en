---
product: campaign
title: Campaign web components and version 100 in Chrome and Firefox browsers
description: Campaign web components and version 100 in Chrome and Firefox browsers
---
# Campaign web components and version 100 in Chrome and Firefox browsers {#version-100}

## What {#what-version-100}

Google and Mozilla are warning that Chrome and Firefox may break some websites due to their upcoming 3-digit versions.
The change in the version number from 2 to 3 digits may cause some problems when visiting websites that are not prepared for this change. Some web pages may stop displaying correctly in the these new browser versions.

Mozilla and Google are testing the compatibility of major websites ahead of time. If there are issues with sites that they cannot fix before these versions are released, both have backup plans ready to ensure the sites are not affected.

## Why {#why-version-100}

Potential problems or loss of functionality on web site originate from the user agent string that browsers send to websites you are visiting : the user agent is a string sent by the browser to the website to let the site know which browser and version you are using, and associated technology. When your browser sends a request to a website, it identifies itself with the user agent string before it retrieves the content you requested. The data in the user agent string help the website to deliver the content in a format that suits your browser. The version of the user agent is incremented to match the browser version number. Moving from 2 to 3-digits can cause issues.

## When {#when-version-100}

Chrome v100 is set for release on **March 29, 2022**, and Firefox v100 on **May 3, 2022**.

## Where {#where-version-100}

Adobe recommends you to test your Campaign web applications, including web forms and surveys, and email mirror pages, to make sure they will still work fine with these new browser versions. 

This recommendation applies to all web applications, and especially if you have included JavaScript code. 

You must check both with Firefox and Chrome, mobile and desktop.

## How {#how-version-100}

In Chrome and Firefox Nightly, you can configure the browser to report the version as 100 right now and correct any issues you come across.

### Firefox 100{#test-firefox-100}

To test your web pages with Mozilla Firefox 100, you can simulate the upcoming user agent change on your web apps by manually changing your user agent string.

1. Open Firefox, enter `about:config` in the address bar, and press enter.
1. Search for `general.useragent.override`.
1. Select 'String' and then click on the plus (+) sign.
    
    ![](assets/force-user-agent-firefox.png) 

1. Enter the following text in the field: 

    ```
    Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
    ```

1. Click on the blue checkmark button to save the setting.
1. Close and relaunch the browser.

With these settings, the browser sends the new user agent string to websites, indicating that the browser is Firefox 100. If you run into any issues with your web forms, you should create a new bug report for Mozilla. Consider rebuilding these web forms before this change is broadly available.

To change your user agent back to its default, simply go back into `about:config` and search for `general.useragent.override` setting again.  When it appears, click on the trash icon to delete the setting, and relaunch the browser.

### Chrome 100{#test-chrome-100}

To test the Google Chrome 100 user agent on your own web apps, you can enable this test using the following steps:

1. Open Chrome, enter `chrome://flags` in the address bar, and press enter.
1. Search `Force major version to 100 in User-Agent` in the search field, and enable it as shown below.

    ![](assets/force-user-agent-chrome.png) 

1. Close and relaunch the browser.
1. Close the `chrome://flags` screen.

With these settings, the browser sends the new user agent string to websites, indicating that the browser is Chrome 100. If you run into any issues with the websites you visit, you should create a new bug report for Google. Consider rebuilding these web forms before this change is broadly available.

To change user agent back to its default, simply follow this process and change the flag's setting to `Default` and relaunch the browser.
