---
product: campaign
title: Recommendations
description: Recommendations
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
TQID: https://experienceleague.adobe.com/hz0wmjq8MEpmen-C30F0tHt5-sRXjQAJ6vaie3hjfAo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring (Campaign)
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines (Campaign)
---
# Recommendations{#recommendations}



Adobe Campaign is a highly transactional system (OLTP database). This means that the underlying database will be frequently updated, leading to a degradation of performance over time. To avoid this type of issue, regular database maintenance is necessary.

>[!IMPORTANT]
>
>A database will only perform optimally if it is maintained on a regular basis. The automatic maintenance offered by some RDBMS is not sufficient and does not replace in-depth maintenance, as for any relational database transactional management systems.
>  
>Procedures described in this document are recommendations. Maintenance plans are the responsibility of your database administrator, who must be your first contact in case of problems.
