---
product: campaign
title: v6.02 中的特定設定
description: v6.02 中的特定設定
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 7e8f8488-f3ef-4b64-9981-335d67caf372
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---

# v6.02 中的特定設定{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

下節詳細說明從v6.02遷移時需要的其他配置。您也應配置 [一般配置](../../migration/using/general-configurations.md) 區段。

## 網站應用程式 {#web-applications}

如果您要從v6.02移轉，可能會出現關於概述類型Web應用程式的錯誤記錄。 錯誤訊息範例：

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

這些Web應用程式使用SQLData，並且由於安全性增強而與v7不相容。 這些錯誤將導致遷移失敗。

如果您未使用這些Web應用程式，請執行下列清除指令碼並重新執行升級後的程式：

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

如果您已修改這些Web應用程式，並且想要在v7中繼續使用這些應用程式，則必須激活 **allowSQLInjents** 選項，然後重新啟動升級後版本。 請參閱 [SQLData](../../migration/using/general-configurations.md#sqldata) 一節以取得詳細資訊。

## 用戶友好性：首頁和導覽 {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>如果您想要繼續使用v6.02概觀類型的Web應用程式，必須啟動 **allowSQLInjents** 選項（在升級後之前）。 請參閱 [網路應用程式](#web-applications).

從6.02版移轉後，Adobe Campaign v6.02首頁不再顯示，但仍可存取，且與Adobe Campaign v7相容。

若要繼續使用v6.02首頁，您必須在移轉後安裝「相容性」套件。

要執行此操作，請導入相容性包：

按一下 **[!UICONTROL Tools > Advanced > Import package]** 並選擇 **campaignMigration.xml** 封裝 **`\nl\datakit\nms\[Your language]\package\optional`**.

要允許訪問v6.02 Web應用程式類型介面，請 **sessionTokenOnly** 伺服器配置選項必須在 **serverConf.xml** 檔案：

```
sessionTokenOnly="true"
```

此選項會更改安全級別以確保介面相容性。

安裝套件後，Adobe Campaign v7首頁會取代為您舊的v6.02首頁，並包含v7的一般設定（藍色首頁橫幅）。

![](assets/dashboards.png)

此首頁上的所有連結都會連結至v7畫面，但清單除外(**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]**&#x200B;等) 連結至v6.02概述（Web應用程式）。

![](assets/dashboards2.png)

如果您想要新增另一個v6.02中設定的概述，您需要從控制面板將其新增至首頁。(**[!UICONTROL Administration > Access management > Dashboard]**)。

>[!NOTE]
>
>請記得中斷連線，然後重新連線主控台以註冊修改。

## 訊息中心 {#message-center}

在Message Center控制實例遷移後，必須重新發佈交易式消息模板，以便它們正常工作。

在v7中，執行例項上的交易式訊息範本的名稱已變更。 它們目前會加上前置詞運算子名稱，此名稱對應至建立它們的控制例項，例如 **control1_template1_rt** (其中 **control1** 是運算子的名稱)。 如果您有大量範本，建議您在控制執行個體上刪除舊範本。
