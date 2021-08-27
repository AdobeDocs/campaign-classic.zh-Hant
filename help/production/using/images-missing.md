---
product: campaign
title: 影像遺失
description: 影像遺失
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# 影像遺失{#images-missing}

![](../../assets/v7-only.svg)

在17.9版中，已移動數個檔案（尤其是圖示）。

對於托管客戶，則沒有影響。 若為內部部署安裝，請閱讀以下內容。

**Apache使用者：**

如果Apache使用者使用提供的&#x200B;**apache_neolane.conf**，則不會影響使用者。

**IIS用戶：**

若為IIS使用者（在Windows上），建置更新後主控台中將缺少數個圖示。 需要執行其他IIS更新步驟：

1. 建置更新後，按兩下位於Campaign安裝目錄中的&#x200B;**iis_neolane_setup.vbs**。 預設路徑為C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新啟動上一步更新的IIS站點。
