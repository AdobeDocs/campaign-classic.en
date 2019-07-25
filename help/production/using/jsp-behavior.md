---
title: JSP behavior
seo-title: JSP behavior
description: JSP behavior
seo-description: 
page-status-flag: never-activated
uuid: afafd744-6d35-435e-9e39-f30b7a65c4aa
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 8f937788-255e-4faf-94db-7e3b21f5a7d2
index: y
internal: n
snippet: y
---

# JSP behavior{#jsp-behavior}

If certain **jsp** jobs are not successfully executed, you must force them to recompile.

For this, enter the following commands:

```
nlserver stop web
cd nl6/tomcat-7
rm -r work/
nlserver start web
```

The **jsp** jobs are regenerated the next time you connect.
