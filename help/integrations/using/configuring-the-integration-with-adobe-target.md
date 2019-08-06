---
title: Configuring the integration with Adobe Target
seo-title: Configuring the integration with Adobe Target
description: Configuring the integration with Adobe Target
seo-description: 
page-status-flag: never-activated
uuid: 58ec0d21-8f59-4b41-a899-d11e0427f1ce
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: bae37cf1-d55f-4d3e-a173-942f4906650e
index: y
internal: n
snippet: y
---

# Configuring the integration with Adobe Target{#configuring-the-integration-with-adobe-target}

## Prerequisites {#prerequisites}

In order to use the integration between Adobe Campaign and Adobe Target, you must have:

* Adobe Experience Cloud and Adobe Target organizations
* An Adobe Target rawbox specified to establish the connection with Adobe Campaign

## Configuring Adobe Campaign {#configuring-adobe-campaign}

To configure Adobe Campaign:

1. Install the **Integration with the Adobe Experience Cloud** standard package. Installing an integration package is the same as installing a standard package, which is detailed in the [Package Import](../../platform/using/working-with-data-packages.md#importing-packages) section. This gives you access to the shared assets via Digital Asset Manager.
1. Enable connection via IMS (Adobe ID connection service) to use images shared via Adobe Experience Cloud in your emails. Consult the section about [IMS](../../integrations/using/about-adobe-id.md).
1. In **Administration > Platform > Options**, configure the server and organization (Tenant) options for Adobe Target:

    * **TNT_EdgeServer**: Adobe Target server used for the integration. This option is already selected by default. This value corresponds to the Adobe Target **Domain Server**, followed by the value **/m2**. For example: **tt.omtrdc.net/m2**.
    * **TNT_TenantName**: Adobe Target Organization name. This value corresponds to the name of the Adobe Target **Client**.

   ![](assets/tar_options.png)

