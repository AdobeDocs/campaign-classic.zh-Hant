---
solution: Campaign Classic
product: campaign
title: 影像遺失
description: 影像遺失
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 5%

---


# 影像遺失{#images-missing}

在17.9版本中，已移動數個檔案（尤其是圖示）。

對於代管客戶而言，沒有影響。 如需內部部署安裝，請閱讀以下內容。

**Apache使用者：**

如果Apache用戶使用提供的&#x200B;**apache_neolane.conf**，則對他們沒有影響

**IIS使用者：**

對於IIS使用者（在Windows上），在建立更新後，主控台中將會遺失數個圖示。 需要其他IIS更新步驟：

1. 在建立更新後，按兩下位於促銷活動安裝目錄中的&#x200B;**iis_neolane_setup.vbs**。 預設路徑為C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新啟動已通過上一步更新的IIS站點。

