---
product: campaign
title: 影像遺失
description: 影像遺失
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 5%

---

# 影像遺失{#images-missing}



在17.9版本中，已移動數個檔案（尤其是圖示）。

對於託管客戶則沒有影響。 對於內部部署安裝，請閱讀以下內容。

**Apache使用者：**

如果Apache使用者使用提供的&#x200B;**apache_neolane.conf**，則不會對其造成影響。

**IIS使用者：**

對於IIS使用者（在Windows上），在建置更新後，主控台中會顯示數個圖示。 需要其他IIS更新步驟：

1. 組建更新後，連按兩下Campaign安裝目錄中的&#x200B;**iis_neolane_setup.vbs**。 預設路徑為C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新啟動上一步驟更新的IIS網站。
