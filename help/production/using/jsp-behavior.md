---
solution: Campaign Classic
product: campaign
title: JSP 行為
description: JSP 行為
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---


# JSP 行為{#jsp-behavior}

如果某 **些jsp** 作業未成功執行，則必須強制它們重新編譯。

為此，輸入以下命令：

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

下次連 **接時** ，將重新生成jsp作業。
