---
product: campaign
title: 移轉至 Adobe Campaign 7 的必要條件
description: 移轉至 Adobe Campaign 7 的必要條件
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# 移轉至 Adobe Campaign 7 的必要條件{#prerequisites-for-migration-to-adobe-campaign}

在執行任何遷移之前，請參閱[開始遷移之前](../../migration/using/before-starting-migration.md)和[配置平台](../../migration/using/configuring-your-platform.md)部分。

從v6.02移轉至Adobe Campaign v7時，某些預先傳送的檔案不會傳送。

如果出現用戶端錯誤，您必須使用新的Adobe Campaign v7程式碼更新控制面板，或手動將下列檔案從v6.02執行個體複製到v7執行個體：

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
