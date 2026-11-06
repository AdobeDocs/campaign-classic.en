---
keywords: Campaign Classic;home;popular topics
product: campaign
title: Adobe Campaign Classic v7 product documentation
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Campaign Classic v7 Documentation {#campaign-classic-documentation}

This documentation covers Campaign Classic v7 for **on-premise and hybrid** deployments: installation, configuration, upgrades, operations and the features that are specific to v7. If your instance is hosted by Adobe (Managed Cloud Services), refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/campaign-home){target="_blank"}. Content that Campaign v8 documents in the same way is no longer duplicated here: see [From v7 to v8](#from-v7-to-v8).

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## What's New

Get a glimpse of the newest enhancements in Adobe Campaign Classic v7 product and documentation! For a comprehensive list of features, improvements, and fixes, check out the detailed [Release Notes](rn/using/latest-release.md). 

>[!BEGINTABS]


>[!TAB October 2026 release is live!] 

The Campaign Classic v7.4.5 - October '26 build (Build 9420) delivers fixes for the Analytics external account, deliveries stuck in the personalization pending status, server CPU usage, intermittent data model update failures, the spam check error in delivery creation and the quarantine of recurring soft bounces.

[![image](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB Move to Adobe IMS]

To reinforce security and authentication process, Adobe Campaign highly recommends to migrate end user authentication mode from the login/password native authentication to Adobe Identity Management System (IMS).

[![image](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## Start with the basics

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>Launch Adobe Campaign</strong><br/>Learn how to launch the Campaign Client console and connect to your Campaign application server(s).</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>Add & manage profiles</strong><br/>Explore profile management in the Adobe Campaign v7 database with ease. Add profiles manually or through imports, refining customer data and customizing campaigns effortlessly.</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>Automate with workflows</strong><br/>Learn how to leverage workflow to design processes including segmentation, campaign execution, file processing, human participation, among others.
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>Create deliveries</strong><br/>Learn how to send messages across various channels such as email, SMS, push notifications etc.</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## Explore the documentation

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-start.svg" width="35px">
    <br/>
      <strong>Get started</strong><br/><a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">User interface</a> (Campaign v8 documentation) - <a href="platform/using/launching-adobe-campaign.md">Connect to Campaign</a> - <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/import" target="_blank">Import & export data</a> (Campaign v8 documentation) - <a href="platform/using/access-management.md">Permissions</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-experience.svg" width="35px">
    <br/>
      <strong>Customer's experience</strong><br/><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank">Automate with workflows</a> (Campaign v8 documentation) - <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html" target="_blank">Marketing campaign</a> - <a href="interaction/using/interaction-and-offer-management.md">Interaction & offer management</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">Reporting</a> (Campaign v8 documentation)
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
    <br/>
      <strong>Send messages</strong><br/><a href="delivery/using/communication-channels.md">Communication channels</a> - <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-message" target="_blank">Send proofs</a> (Campaign v8 documentation) - <a href="delivery/using/get-started-a-b-testing.md">A/B testing</a> - <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">Message tracking</a> - <a href="delivery/using/about-deliverability.md">Deliverability</a> - <a href="message-center/using/about-transactional-messaging.md">Transactional messaging</a>
    </td>
  </tr>
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon_profile-audience.svg" width="35px">
      <br/>
      <strong>Profiles & audiences</strong><br/> <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">Create lists</a> (Campaign v8 documentation) - <a href="delivery/using/about-services-and-subscriptions.md">Services & subscriptions</a> - <a href="platform/using/privacy-management.md">Privacy & consent</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>Architecture & configuration</strong><br/><a href="production/using/general-architecture.md">Architecture principles</a> - <a href="production/using/build-upgrade.md">Performing a build upgrade</a> - <a href="production/using/configuration.md">Configure Campaign</a> - <a href="installation/using/external-accounts.md">Connect to external systems</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>Developer resources</strong><br/><a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/datamodel" target="_blank">Data model description</a> (Campaign v8 documentation) - <a href="configuration/using/about-schema-reference.md">Schema structure</a> - <a href="configuration/using/editing-forms.md">Input forms</a> - <a href="configuration/using/about-web-services.md">APIs</a> - <a href="https://experienceleague.adobe.com/en/tools/campaign-api">JSAPI Reference Documentation</a> - <a href="configuration/using/about-custom-recipient-table.md">Custom recipient table</a>
    </td>
  </tr>
</table> 

## From v7 to v8 {#from-v7-to-v8}

Content that is documented in the Campaign v8 documentation has been removed from the v7 documentation. Use this table to find it.

| If you are looking for... | Go to the Campaign v8 documentation |
| --- | --- |
| The user interface | [Discover the user interface](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| Profiles, lists, import and export | [Import profiles and data](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/import){target="_blank"} |
| Workflows | [About workflows](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| Marketing campaigns | [Get started with marketing campaigns](https://experienceleague.adobe.com/en/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| Creating and sending deliveries | [Create a message](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| Built-in reports | [Get started with reporting](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| Permissions | [Get started with permissions](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| Input forms | [Get started with input forms](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## Additional resources

[Adobe Campaign Product Description](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} - [Compatibility matrix](rn/using/compatibility-matrix.md) - [Tutorials](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html){target="_blank"} - [Control Panel for Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html){target="_blank"} - [Email Tracking Pixels and CNIL Guidance](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}
