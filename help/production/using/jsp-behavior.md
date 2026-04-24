---
product: campaign
title: JSP behavior
description: JSP behavior
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
TQID: https://experienceleague.adobe.com/IQSjBaSbnZcsqs0glv8z1aIwOBbtVO2roeXlJiYgEfo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
---
# JSP behavior{#jsp-behavior}



If certain **jsp** jobs are not successfully executed, you must force them to recompile.

For this, enter the following commands:

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

The **jsp** jobs are regenerated the next time you connect.
