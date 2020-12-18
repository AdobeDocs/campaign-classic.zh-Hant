---
solution: Campaign Classic
product: campaign
title: 移轉至 Adobe Campaign 7 的必要條件
description: 移轉至 Adobe Campaign 7 的必要條件
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---


# 移轉至 Adobe Campaign 7 的必要條件{#prerequisites-for-migration-to-adobe-campaign}

在運行任何遷移之前，請參考[開始遷移前](../../migration/using/before-starting-migration.md)和[配置平台](../../migration/using/configuring-your-platform.md)部分。

從v6.02移轉至Adobe Campaign v7時，無法傳送某些預先傳送的檔案。

如果出現用戶端錯誤，您必須使用新的Adobe Campaign v7程式碼更新控制面板，或手動將下列檔案從v6.02例項複製到v7例項：

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
