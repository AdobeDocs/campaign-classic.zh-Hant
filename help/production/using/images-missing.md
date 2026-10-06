---
product: campaign
title: 影像遺失
description: 影像遺失
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: 'https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '111'
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
