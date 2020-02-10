---
title: 影像遺失
seo-title: 影像遺失
description: 影像遺失
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 影像遺失{#images-missing}

在17.9版本中，已移動數個檔案（尤其是圖示）。

對於代管客戶而言，沒有影響。 如需內部部署安裝，請閱讀以下內容。

**Apache使用者：**

如果Apache用戶使用提供的 **apache_neolane.conf，則對他們沒有影響**

**IIS使用者：**

對於IIS使用者（在Windows上），在建立更新後，主控台中將會遺失數個圖示。 需要其他IIS更新步驟：

1. 在建立更新後，按兩下位於 **Campaign安裝目錄中的iis_neolane_setup.vbs** 。 預設路徑為C:Program Files(x86)AdobeAdobe Campaign v7tomcat-7conf
1. 重新啟動已通過上一步更新的IIS站點。

