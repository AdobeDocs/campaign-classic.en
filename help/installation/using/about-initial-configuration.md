---
product: campaign
title: About initial configuration
description: About initial configuration
feature: Installation, Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
TQID: 'https://experienceleague.adobe.com/rQT-wcpjGzyYfEV3thGlY0WD7Po-A08yD0pGMr13p7s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
---
# Key steps to configure and deploy your instance{#about-initial-configuration}



Once the Adobe Campaign installation is complete, you need to configure it to make sure it operates efficiently with your constraints and technical architecture. The steps for configuring an Adobe Campaign instance are detailed in this chapter, in the following sequence:

1. Create the instance and the related connection, refer to [Creating an instance and logging on](../../installation/using/creating-an-instance-and-logging-on.md).
1. Create and configure the database, refer to [Creating and configuring the database](../../installation/using/creating-and-configuring-the-database.md).
1. Configure the Adobe Campaign server, refer to [Campaign server configuration](../../installation/using/configuring-campaign-server.md).
1. Deploy the instance, refer to [Deploying an instance](../../installation/using/deploying-an-instance.md).

Configuring the instance implies enabling processes (web, mta, wfserver, etc.) to be started on the server and configuring modules for sending email, for tracking, etc. For each instance, Adobe Campaign processes are activated on the server. For more on this, refer to [this section](../../installation/using/configuring-campaign-server.md#enabling-processes).

Additional configurations can be required for each instance (depending on the modules used, your architecture and your needs) to optimize Adobe Campaign operation.
