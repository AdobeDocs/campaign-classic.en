---
product: campaign
title: Personalization and privacy
description: Learn security best practices for privacy and personalization
feature: Installation, Privacy, Privacy Tools, URL Personalization
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
---
# Personalization and privacy {#privacy}




## URL Personalization {#url-personalization}

When adding personalized links to your content, always avoid having any personalization in the hostname part of the URL to avoid potential security gaps. The following examples should never be used in all URL attributes <`a href="">` or `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recommendation

To validate and ensure that you are not using above, run a query on tracking URL table via [Campaign Generic Query Editor](../../platform/using/steps-to-create-a-query.md) or create a workflow with filter criteria in the [query activity](../../workflow/using/query.md).

Example:

1. Create a workflow and add a **Query** activity. [Learn more](../../workflow/using/query.md).

1. Open the **Query** activity and create a filter on the `nmsTrackingUrl` table as follows: 

    `source URL starts with http://<% or source URL starts with https://<%`

1. Run the workflow and check if there are result.

1. If so, open the output transition to view the list of URLs.

    ![](assets/privacy-query-dynamic-url.png)


### URL signature

To improve security, a signature mechanism for tracking links in emails has been introduced. It is available starting the builds 19.1.4 (9032@3a9dc9c) and 20.2. This feature is enabled by default.

>[!NOTE]
>
>When a malformed signed URL is clicked, this error is returned: `Requested URL '…' was not found.`

In addition, you can use an enhancement to disable URLs generated in previous builds. This feature is disabled by default. You can reach out to [Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) to enable this feature.

If you are running on the 19.1.4 build, you may experience issues with push notification deliveries using tracking links, or deliveries using anchor tags. If so, we recommend that you disable URL signature.

As a Campaign hosted, Managed Cloud Services or hybrid customer, you must reach out to [Customer Care](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) to have URL signature disabled.

If you are running Campaign in a hybrid architecture, before you enable URL signature, make sure that the hosted mid-sourcing instance has been upgraded as follows:

* First the on-premise marketing instance
* Then upgrade to the same version as the on-premise marketing instance or to a slightly higher version

Otherwise, some of these issues may occur:

* Before the mid-sourcing instance is upgraded, URLs are sent without signature through this instance.
* After the mid-sourcing instance has been upgraded and URL signature has been enabled on both instances, the URLs that had previously been sent without signature are rejected. The reason is that a signature is requested by the tracking files that have been provided by the marketing instance.

To disable URLs that have been generated in previous builds, follow these steps on all Campaign servers at the same time:

1. In the server configuration file (`serverConf.xml`), change the **blockRedirectForUnsignedTrackingLink** option to **true**.
1. Restart the `nlserver` service.
1. On the `tracking` server, restart the `web` server (apache2 on Debian, httpd on CentOS/RedHat, IIS on Windows).

To enable URL signature, follow these steps on all Campaign servers at the same time:

1. In the server configuration file (`serverConf.xml`), change **signEmailLinks** option, to **true**.
1. Restart the **nlserver** service.
1. On the `tracking` server, restart the `web` server (apache2 on Debian, httpd on CentOS/RedHat, IIS on Windows).

## Data restriction

You must make sure that the encrypted passwords are not accessible by a low privilege authenticated user. To do that, restrict access to password fields only, or to the entire entity (need a build >= 8770).

This restriction allows you to remove passwords fields but let the external account accessible from the interface for all users. [Learn more](../../configuration/using/restricting-pii-view.md).

To perform this, follow the steps below:

1. Browse to the **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** folder of Campaign explorer.

1. Create a data schema, as an **[!UICONTROL Extension of a schema]**.

    ![](assets/privacy-data-restriction.png)

1. Choose **[!UICONTROL External Account]** (extAccount).

1. In the last wizard screen, edit your new 'srcSchema' to restrict access to all password fields:

    You can replace the main element (`<element name="extAccount" ... >`) by:

    ```sql
    <element name="extAccount">
        <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
        <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
        <element name="s3Account">
            <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
        </element>
        <element name="wapPush">
            <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
            <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
        </element>
        <element name="mms">
            <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
            <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
        </element>
    </element>
    ```

    So your extended srcSchema can look like:

    ```sql
    <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
                desc="Definition of external accounts (Email, SMS...) used by the modules"
                entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
                labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
                mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
                name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
        <createdBy _cs="Administrator (admin)"/>
        <modifiedBy _cs="Administrator (admin)"/>
        <element name="extAccount">
            <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
            <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
  
            <element name="s3Account">
                <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
            </element>
            <element name="wapPush">
                <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
                <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
            </element>
            <element name="mms">
                <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
                <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
            </element>
        </element>
    </srcSchema>    
    ```

    >[!NOTE]
    >
    >You can replace `$(loginId) = 0 or $(login) = 'admin'` with `hasNamedRight('admin')` to allow all users with admin rights to see these passwords.

## Protect pages with PI

We strongly advise on-premise customers to protect the pages that might contain personal information (PI) such as mirror pages, web applications, etc.

The goal of this procedure is to prevent these pages from being indexed, thus avoiding a potential security risk. Here are a few useful articles:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

To protect your pages, follow these steps:

1. Add a `robots.txt` file at the root of your web server (Apache or IIS). Here is the content of the file:

    ```sql
    # Make changes for all web spiders
    User-agent:
    *Disallow: /
    ```

    For IIS, refer to [this page](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

    For Apache, you can place the file in **/var/www/robots.txt** (Debian).

1. Sometimes adding a **robots.txt** file is not sufficient in terms of security. For example, if another website contains a link to your page, it might appear in a search result.

    In addition to the **robots.txt** file, it is advised to add a **X-Robots-Tag** header. You can do it in Apache or IIS and in the **serverConf.xml** configuration file.

    For more information, refer to [this article](https://developers.google.com/search/reference/robots_meta_tag).


## Privacy Requests

Refer to [this page](../../platform/using/privacy-management.md) for general information on what Privacy Management is and the implementation steps in Adobe Campaign. You will also find best practices and an overview of the user process and personas.  
