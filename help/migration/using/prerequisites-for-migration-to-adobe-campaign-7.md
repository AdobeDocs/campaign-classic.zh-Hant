---
title: 移轉至Adobe Campaign 7的先決條件
seo-title: 移轉至Adobe Campaign 7的先決條件
description: 移轉至Adobe Campaign 7的先決條件
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# 移轉至Adobe Campaign 7的先決條件{#prerequisites-for-migration-to-adobe-campaign}

在執行任何移轉之前，請先參 [閱「開始移轉](../../migration/using/before-starting-migration.md) 」 [和「設定平台」章節](../../migration/using/configuring-your-platform.md) 。

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
