---
product: campaign
title: Recommendations
description: Recommendations
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
---
# Recommendations{#recommendations}

![](../../assets/v7-only.svg)

Adobe Campaign is a highly transactional system (OLTP database). This means that the underlying database will be frequently updated, leading to a degradation of performance over time. To avoid this type of issue, regular database maintenance is necessary.

>[!IMPORTANT]
>
>A database will only perform optimally if it is maintained on a regular basis. The automatic maintenance offered by some RDBMS is not sufficient and does not replace in-depth maintenance, as for any relational database transactional management systems.
>  
>Procedures described in this document are recommendations. Maintenance plans are the responsability of your database administrator, who must be your first contact in case of problems.
