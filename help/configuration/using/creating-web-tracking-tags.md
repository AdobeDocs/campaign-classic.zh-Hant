---
product: campaign
title: 建立Web跟蹤標籤
description: 瞭解如何建立Web跟蹤標籤
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# 建立Web跟蹤標籤{#creating-web-tracking-tags}

![](../../assets/v7-only.svg)

您要跟蹤的網站的每一頁都必須在您的Adobe Campaign平台中引用。 此引用可通過兩種方式執行：

1. 要跟蹤的URL的手動定義，
1. 要跟蹤的URL的即時建立。

## 定義要在應用程式中跟蹤的URL {#defining-the-urls-to-be-tracked-in-the-application}

此方法允許您手動定義要跟蹤的頁面，然後生成關聯的Web跟蹤標籤的示例。 此操作在 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 客戶端控制台的節點。

![](assets/d_ncs_integration_webtracking_screen.png)

要生成要插入頁面的HTML代碼，請執行以下操作：

* 輸入標籤的標籤：會在跟蹤日誌中顯示，
* 指示源URL:此欄位僅供參考，並允許您指明跟蹤的頁面（可選）,
* 如果需要，請輸入有效期，
* 按一下 **[!UICONTROL Generate]** HTML代碼。

然後複製生成的代碼並將其貼上到要跟蹤的頁面中。

## 要跟蹤的URL的即時建立 {#on-the-fly-creation-of-urls-to-be-tracked}

通過向Web跟蹤URL的值添加資訊，可以即時建立Web跟蹤URL **標籤** 參數：

* 跟蹤的頁面類型：「w」表示WEB，「t」表示TRANSACTION,
* 必須在其中建立URL的資料夾的內部名稱。

以下兩條資訊必須通過添加字元「|」與跟蹤頁的標識符相連：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>切記編碼 **標籤** 參數。

**示例**:建立事務類型Web跟蹤URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
