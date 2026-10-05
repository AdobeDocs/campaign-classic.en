---
product: campaign
title: Prerequisites of Campaign installation in Windows
description: Prerequisites of Campaign installation in Windows
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
TQID: 'https://experienceleague.adobe.com/vECxz7-bt6DMteRM-N4BtD6Uo5qonHrkgQQeEOkTSt0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
---
# Get started with installing Campaign on Windows {#prerequisites-of-campaign-installation-in-windows}



The technical configuration and software needed to install Adobe Campaign is presented in the [Compatibility matrix](../../rn/using/compatibility-matrix.md).

The Adobe Campaign server installation process for multi-instance usage is described below in [Installing the server](../../installation/using/installing-the-server.md).

The main steps are as follows:

1. Install the application server, refer to [Executing the installation program](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrate with a Web server (optional, depending on the components deployed), refer to [Configuring the IIS Web server](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Once the installation steps are complete, you need to configure the instances, the database and the server. For more on this, refer to [About initial configuration](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>When Adobe Campaign is deployed to a Windows environment, users with the necessary access rights can use UNC syntax (Universal.Uniform Naming Convention) for access paths during file manipulation on the network.
