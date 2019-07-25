---
title: Configuring the integration with Adobe Target
seo-title: Configuring the integration with Adobe Target
description: Configuring the integration with Adobe Target
seo-description: 
page-status-flag: never-activated
uuid: 2388298c-209f-45b2-af85-02a47b80b7e9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 79f65df3-e0db-4bf2-ad8e-054b343c3f8a
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

1. Install the **Integration with the Adobe Experience Cloud** standard package. Installing an integration package is the same as installing a standard package, which is detailed in the [Package Import](/platform/using/working-with-data-packages.md#importing-packages) section. This gives you access to the shared assets via Digital Asset Manager.
1. Enable connection via IMS (Adobe ID connection service) to use images shared via Adobe Experience Cloud in your emails. Consult the section about [IMS](../../integrations/using/about-adobe-id.md).
1. In **Administration > Platform > Options**, configure the server and organization (Tenant) options for Adobe Target:

    * **TNT_EdgeServer**: Adobe Target server used for the integration. This option is already selected by default. This value corresponds to the Adobe Target **Domain Server**, followed by the value **/m2**. For example: **tt.omtrdc.net/m2**.
    * **TNT_TenantName**: Adobe Target Organization name. This value corresponds to the name of the Adobe Target **Client**.

   ![](assets/tar_options.png)

