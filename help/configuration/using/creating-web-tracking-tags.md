---
product: campaign
title: 建立網路追蹤標籤
description: 建立網路追蹤標籤
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---

# 建立網路追蹤標籤{#creating-web-tracking-tags}

您要追蹤的網站每個頁面都必須在Adobe Campaign平台中參考。 此參考可透過兩種方式執行：

1. 手動定義要追蹤的URL,
1. 即時建立要追蹤的URL。

## 定義應用程式{#defining-the-urls-to-be-tracked-in-the-application}中要追蹤的URL

此方法可讓您手動定義要追蹤的頁面，然後產生相關網頁追蹤標籤的範例。 此操作在客戶端控制台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;節點中定義。

![](assets/d_ncs_integration_webtracking_screen.png)

若要產生要插入頁面中的HTML程式碼：

* 輸入標籤：會顯示在追蹤記錄中，
* 指示源URL:此欄位僅供參考，可讓您指出追蹤的頁面（選用）、
* 如果需要，請輸入有效期，
* 按一下&#x200B;**[!UICONTROL Generate]** HTML代碼。

然後複製產生的程式碼，並貼到要追蹤的頁面中。

## 要追蹤的URL即時建立{#on-the-fly-creation-of-urls-to-be-tracked}

您可以借由將資訊新增至&#x200B;**tagid**&#x200B;參數的值，即時建立網頁追蹤URL:

* 追蹤的頁面類型：「w」表示WEB，「t」表示TRANSACTION,
* 必須建立URL的資料夾的內部名稱。

必須新增字元「|」，將這兩項資訊與追蹤頁面的識別碼串連：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>請記得將&#x200B;**tagid**&#x200B;參數當作URL參數時編碼。

**範例**:建立交易類型網頁追蹤URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
