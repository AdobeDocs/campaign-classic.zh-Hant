---
solution: Campaign Classic
product: campaign
title: v6.02 中 的特定配置
description: v6.02 中 的特定配置
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---


# v6.02 中 的特定配置{#specific-configurations-in-v6-02}

下節詳細說明從v6.02移轉時需要的其他設定。您還應配置[General configurations](../../migration/using/general-configurations.md)部分中詳細說明的設定。

## 網頁應用程式{#web-applications}

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

如果您已修改這些Web應用程式，並想要在v7中繼續使用它們，則必須在不同的安全區中啟動&#x200B;**allowSQLInjeption**&#x200B;選項，然後重新啟動postupgrade。 有關詳細資訊，請參閱[SQLData](../../migration/using/general-configurations.md#sqldata)部分。

## 用戶友好：首頁和導覽{#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>如果您想繼續使用v6.02 overview-type Web應用程式，則必須在設定升級前，在不同的安全區中啟動&#x200B;**allowSQLInjeption**&#x200B;選項。 請參閱[Web應用程式](#web-applications)。

從6.02版移轉後，Adobe Campaign 6.02版首頁不再顯示，但仍可存取且與Adobe Campaign v7相容。

若要繼續使用v6.02首頁，您必須在移轉後安裝「相容」套件。

要執行此操作，請導入相容性包：

按一下&#x200B;**[!UICONTROL Tools > Advanced > Import package]**，然後在&#x200B;**`\nl\datakit\nms\[Your language]\package\optional`**&#x200B;中選擇&#x200B;**campaignMigration.xml**&#x200B;套件。

若要允許存取v6.02 Web應用程式類型介面，**sessionTokenOnly**&#x200B;伺服器組態選項必須在&#x200B;**serverConf.xml**&#x200B;檔案中啟動：

```
sessionTokenOnly="true"
```

此選項可更改安全級別以確保介面相容性。

在安裝套件後，Adobe Campaign v7首頁會由舊版v6.02首頁取代，其中包含v7的一般設定（藍色首頁橫幅）。

![](assets/dashboards.png)

此首頁上的所有連結都會連結至v7畫面，但清單除外（**[!UICONTROL operation list]**、**[!UICONTROL delivery tracking in operations]**&#x200B;等） 連結至v6.02概觀（Web應用程式）。

![](assets/dashboards2.png)

如果您想要新增另一個v6.02中設定的概觀，您必須從控制面板將它新增至首頁。(**[!UICONTROL Administration > Access management > Dashboard]**)。

>[!NOTE]
>
>請記得斷開連接，然後重新連接控制台以註冊修改。

## 消息中心{#message-center}

在消息中心控制實例遷移後，您必須重新發佈事務性消息模板，以使其工作。

在v7中，執行實例上的事務性消息模板的名稱已經更改。 它們目前由與其所建立的控制例項相對應的運算子名稱前置詞，例如&#x200B;**control1_template1_rt**（其中&#x200B;**control1**&#x200B;是運算子的名稱）。 如果您有大量範本，建議您在控制例項上刪除舊範本。
