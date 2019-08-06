---
title: JSP behavior
seo-title: JSP behavior
description: JSP behavior
seo-description: 
page-status-flag: never-activated
uuid: e3be639b-e7e7-4d70-8c73-5b640cc7942d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: ccc62b9c-d96e-47e3-b01a-7e7484677933
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
