---
title: v6.02中的特定配置
seo-title: v6.02中的特定配置
description: v6.02中的特定配置
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# v6.02中的特定配置{#specific-configurations-in-v6-02}

下節詳細說明從v6.02移轉時需要的其他設定。您還應配置「常規配置」部分中詳 [細的設定](../../migration/using/general-configurations.md) 。

## 網頁應用程式 {#web-applications}

如果您要從v6.02移轉，可能會出現與概述類型Web應用程式相關的錯誤記錄。 錯誤消息示例：

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

這些Web應用程式使用SQLData，由於安全性的提升而與v7不相容。 這些錯誤將導致遷移失敗。

如果您未使用這些Web應用程式，請執行下列清除指令碼並重新執行Postupgrade:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

如果您已修改這些Web應用程式，並想要在v7中繼續使用它們，則必須在不同的安全區中啟用 **allowSQLInjeption** 選項，然後重新啟動postupgrade。 有關此的詳 [細資訊，請參見SQLData](../../migration/using/general-configurations.md#sqldata) 部分。

## 用戶友好：首頁和導覽 {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>如果您想要繼續使用v6.02概觀類型的Web應用程式，則必須在配置升級之前，在不同的安全區中啟用 **allowSQLInjeption** 選項。 請參閱 [Web應用程式](#web-applications)。

從6.02版移轉後，Adobe Campaign 6.02版首頁不再顯示，但仍可存取且與Adobe Campaign v7相容。

若要繼續使用v6.02首頁，您必須在移轉後安裝「相容」套件。

要執行此操作，請導入相容性包：

按一 **[!UICONTROL Tools > Advanced > Import package]** 下，然後在 **中選擇campaignMigration.xml** 套件 **`\nl\datakit\nms\[Your language]\package\optional`**。

若要允許存取v6.02 web應用程式類型介面， **sessionTokenOnly** server組態選項必須在 **** serverConf.xml檔案中啟動：

```
sessionTokenOnly="true"
```

此選項可更改安全級別以確保介面相容性。

在安裝套件後，Adobe Campaign v7首頁會由舊版v6.02首頁取代，其中包含v7的一般設定（藍色首頁橫幅）。

![](assets/dashboards.png)

此首頁上的所有連結都會連結至v7畫面，但清單(**[!UICONTROL operation list]**、 **[!UICONTROL delivery tracking in operations]**&#x200B;等等)除外連結至v6.02概觀（Web應用程式）。

![](assets/dashboards2.png)

如果您想要新增另一個v6.02中設定的概觀，您必須從控制面板將它新增至首頁。(**[!UICONTROL Administration > Access management > Dashboard]**)。

>[!NOTE]
>
>請記得斷開連接，然後重新連接控制台以註冊修改。

## 訊息中心 {#message-center}

在消息中心控制實例遷移後，您必須重新發佈事務性消息模板，以使其工作。

在v7中，執行實例上的事務性消息模板的名稱已經更改。 它們目前由運算子名稱前置詞，此運算子名稱對應於建立它們的控制例項，例如 **control1_template1_rt** (其中 **control1** 是運算子的名稱)。 如果您有大量範本，建議您在控制例項上刪除舊範本。
