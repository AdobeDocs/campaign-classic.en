---
product: campaign
title: Migrate to the Adobe Analytics Connector
description:  Campaign - Analytics Connector FAQ
hide: yes
hidefromtoc: yes
---
# How to migrate to Adobe Analytics Connector {#acc-aa-faq}

Starting Campaign Classic v7 21.1.3 release, the Adobe Analytics Data Connector is deprecated. [Learn more](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

On August 1, 2021, Adobe Campaign Classic will be removed from the legacy Data Connectors UI, however, existing Campaign integrations will continue to collect and pass data to Adobe Analytics until March 1, 2022. On March 1, 2022, the integration will cease to collect and pass data to Adobe Analytics. 

You must migrate to the new Adobe Analytics Connector integration on Adobe Exchange which replaces the legacy Data Connectors Integration, as detailed in [this page](../platform/using/adobe-analytics-connector.md).


>[!NOTE]
>
>For any questions about these changes, read the [FAQ](#faq-aa). For more information, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## What changed?

A new integration between Campaign Classic v7 and Adobe Analytics is now available. Major changes are listed below.

* Integration between Adobe Campaign Classic and Adobe Analytics authentication has moved from user/password to Adobe Identity Management Service (IMS). As a consequence, you must implement Adobe IMS, and connect to Campaign [via an Adobe ID](../integrations/using/about-adobe-id.md), before starting Analytics Connector implementation.

* The **Contact Date** Classification, which use to be of type date, has been deprecated by Adobe Analytics. For migrated integrations, it will still remain of the same type. For any **Contact Date** created by Campaign, the type will be **String**.

* **Processing Rules** are created by Adobe Campaign as part of new integrations. Either **Processing Rules** should be created manually from Adobe Analytics or directly use Client-Side Javascript implementation. **Processing Rules** will remain intact for existing integrations.

* The built-in technical workflows and their behavior remains the same. Only the backend APIs used by the workflows to push/pull data to/from Adobe Analytics have been changed. 

* Note that the `nlserver` process should be configured with the IMS Technical Account User for the new connector to work. This change must be done by Adobe. To have this implemented, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* If you were Adobe Genesis APIs in customised workflows for pulling and pushing the data from Adobe Analytics, you now need to use the new Adobe Analytics 1.4/2.0 APIs. [Learn more](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Are you impacted?

If you are using the existing Adobe Analytics Data Connector (previously known as Genesis integration), and the integration was implemented on a lower build than Campaign 21.1.3, you are impacted.

Learn how to check your version [in this section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## How to update?

You need to upgrade to Campaign 21.1.3 (or more) **before March 1, 2022**.

As a hosted customer, Adobe will be working with you to upgrade your instance(s) to the newer version.

As an on-premise/hybrid customer, you need to upgrade to one of the newer versions to benefit from the new integration.

Once all instances are upgraded, you will be able to [implement the new integration](../platform/using/adobe-analytics-connector.md) to Adobe Analytics Connector, and ensure a seamless transition.


## FAQ{#faq-aa}

**How can I get logs?** 

User interface configuration and workflows are equipped with **verbose** logging.

In verbose mode, request and response headers are also printed for each API request to Adobe Analytics.

As an on-premise user, you can implement the verbose mode as follows:

* To enable verbose mode for the user interface: re-run the `web` process in verbose mode.
* To enable verbose mode for the **webAnalytics** workflows: select the **Execute in the engine** option from the workflow properties, and re-run `wfserver` in verbose mode.

**What does the 'Integration Owner Not Admin' error means?**

Learn more about the Data Connectors `Integration Owner Not Admin` Error in [this page](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Once migration to the new connector is done, what happens to old data and report suites?**

After migration, a new connector (migrated from the old connector) will start pushing data to that same report suite and existing data will not be affected: it will be adding to the existing data.

**Some existing evars/events/report suites present in Analytics are not visible in Campaign. What should I do?**

Integration relies on data on Technical Account Token for day to day operation. If there is missing permission to a dimension/metric/report suite from the product profile associated with Technical Account User, APIs that we use will simply falter for those requests.

If we are reading for details of an Analytics component (like metrics/dimensions/segments/report suites), the API will not return these components in the result (which may look like something got deleted on the Analytics side or is not present). Analytics API will reject those requests and error out. 

The solution is to update the **Product Profile** in Analytics User Context of Technical User Token with the newly created/missing components by adding these components in [Adobe Admin Console](https://adminconsole.adobe.com/). For more guidance, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Useful links

* [Upgrade your environment](../production/using/build-upgrade.md)
* [Build upgrade FAQ](../platform/using/faq-build-upgrade.md)
* [Download Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Make the new Client Console available to users](../installation/using/client-console-availability-for-windows.md)
* [Install Campaign Client Console](../installation/using/installing-the-client-console.md)
