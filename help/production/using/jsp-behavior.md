---
product: campaign
title: JSP 行為
description: JSP 行為
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
TQID: https://experienceleague.adobe.com/IQSjBaSbnZcsqs0glv8z1aIwOBbtVO2roeXlJiYgEfo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 66
ht-degree: 36%

---

# JSP 行為{#jsp-behavior}



如果某些&#x200B;**jsp**&#x200B;工作未成功執行，您必須強制它們重新編譯。

為此，請輸入以下命令：

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

**jsp**&#x200B;工作會在您下次連線時重新產生。
