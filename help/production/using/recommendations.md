---
title: Recommendations
seo-title: Recommendations
description: Recommendations
seo-description: 
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
index: y
internal: n
snippet: y
---

# Recommendations{#recommendations}

Adobe Campaign is a highly transactional system (OLTP database). This means that the underlying database will be frequently updated, leading to a degradation of performance over time. To avoid this type of issue, regular database maintenance is necessary.

>[!CAUTION]
>
>A database will only perform optimally if it is maintained on a regular basis. The automatic maintenance offered by some RDBMS is not sufficient and does not replace in-depth maintenance, as for any relational database transactional management systems.
>  
>Procedures described in this document are recommendations. Maintenance plans are the responsability of your database administrator, who must be your first contact in case of problems.

