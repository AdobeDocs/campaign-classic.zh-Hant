---
product: campaign
title: 影像遺失
description: 影像遺失
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# 影像遺失{#images-missing}



在17.9版本中，已移動數個檔案（尤其是圖示）。

對於託管客戶則沒有影響。 若為內部部署安裝，請閱讀下列內容。

**Apache使用者：**

如果Apache使用者使用提供的，則這對他們沒有任何影響 **apache_neolane.conf**.

**IIS使用者：**

對於IIS使用者（在Windows上），在建置更新後，主控台中會缺少數個圖示。 需要其他IIS更新步驟：

1. 組建更新後，按兩下 **iis_neolane_setup.vbs** 位在Campaign安裝目錄中。 預設路徑為C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. 重新啟動上一步驟更新的IIS網站。
