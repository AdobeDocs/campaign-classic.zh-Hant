---
solution: Campaign Classic
product: campaign
title: 建立網頁追蹤標籤
description: 建立網頁追蹤標籤
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---


# 建立網頁追蹤標籤{#creating-web-tracking-tags}

您要追蹤之網站的每個頁面都必須在您的Adobe Campaign平台中參考。 此引用可通過兩種方式執行：

1. 要追蹤之URL的手動定義、
1. 即時建立要追蹤的URL。

## 定義要在應用程式{#defining-the-urls-to-be-tracked-in-the-application}中追蹤的URL

此方法可讓您手動定義要追蹤的頁面，然後產生相關聯網頁追蹤標籤的範例。 此操作在客戶機控制台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;節點中定義。

![](assets/d_ncs_integration_webtracking_screen.png)

若要產生要插入頁面的HTML程式碼：

* 輸入標籤的標籤：會顯示在追蹤記錄中，
* 指定來源URL:此欄位僅供參考，可讓您指出追蹤的頁面（選用）、
* 如果需要，請輸入有效期，
* 按一下&#x200B;**[!UICONTROL Generate]** HTML程式碼。

然後複製產生的程式碼，並貼入要追蹤的頁面。

## 即時建立要追蹤的URL {#on-the-fly-creation-of-urls-to-be-tracked}

您可以借由新增資訊至&#x200B;**tagid**&#x200B;參數的值，即時建立網頁追蹤URL:

* 追蹤的頁面類型：&#39;w&#39;代表WEB,&#39;t&#39;代表TRANSACTION,
* 必須建立URL的資料夾內部名稱。

這兩項資訊必須與追蹤頁面的識別碼串連，方法是新增字元&#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>當&#x200B;**tagid**&#x200B;參數用作URL參數時，請記得對其值進行編碼。

**範例**:建立交易類型網頁追蹤URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
