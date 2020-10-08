---
title: JSP 行為
seo-title: JSP 行為
description: JSP 行為
seo-description: null
page-status-flag: never-activated
uuid: b9e9f348-968c-46e0-8340-df1f1fcaf3a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 5dcc4090-effe-479e-8d5c-67e6a6542fbb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '38'
ht-degree: 21%

---


# JSP 行為{#jsp-behavior}

如果某 **些jsp** 作業未成功執行，則必須強制它們重新編譯。

為此，輸入以下命令：

```
nlserver stop web
cd nl6/tomcat-7
rm -r work/
nlserver start web
```

下次連 **接時** ，將重新生成jsp作業。
