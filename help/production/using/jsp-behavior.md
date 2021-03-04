---
solution: Campaign Classic
product: campaign
title: JSP behavior
description: JSP behavior
audience: production
content-type: reference
topic-tags: troubleshooting
---

# JSP behavior{#jsp-behavior}

If certain **jsp** jobs are not successfully executed, you must force them to recompile.

For this, enter the following commands:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

The **jsp** jobs are regenerated the next time you connect.
