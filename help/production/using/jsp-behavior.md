---
product: campaign
title: JSP 行為
description: JSP 行為
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP 行為{#jsp-behavior}

![](../../assets/v7-only.svg)

如果確定 **jsp** 作業未成功執行，您必須強制它們重新編譯。

為此，請輸入以下命令：

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

此 **jsp** 下次連接時將重新生成作業。
