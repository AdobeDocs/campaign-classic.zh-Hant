---
product: campaign
title: JSP 行為
description: JSP 行為
feature: Monitoring
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 15%

---

# JSP 行為{#jsp-behavior}



若確定 **jsp** 工作無法成功執行，您必須強制它們重新編譯。

為此，請輸入以下命令：

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

此 **jsp** 下次連線時就會重新產生工作。
