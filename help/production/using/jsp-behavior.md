---
product: campaign
title: JSP 行為
description: JSP 行為
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP 行為{#jsp-behavior}



若確定 **jsp** 作業無法成功執行，您必須強制重新編譯。

為此，請輸入以下命令：

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

此 **jsp** 作業會在您下次連線時重新產生。
