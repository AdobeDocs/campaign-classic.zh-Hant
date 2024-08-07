---
product: campaign
title: 建立網頁追蹤標籤
description: 瞭解如何建立網路追蹤標籤
feature: Application Settings
role: Data Engineer, Developer
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# 建立網頁追蹤標籤{#creating-web-tracking-tags}

您想要追蹤的網站每個頁面，都必須在Adobe Campaign平台中參照。 此參考可透過兩種方式執行：

1. 手動定義要追蹤的URL，
1. 即時建立要追蹤的URL。

## 定義要在應用程式中追蹤的URL {#defining-the-urls-to-be-tracked-in-the-application}

此方法可讓您手動定義要追蹤的頁面，然後產生相關網頁追蹤標籤的範例。 此作業在使用者端主控台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;節點中定義。

![](assets/d_ncs_integration_webtracking_screen.png)

若要產生要插入頁面中的HTML代碼：

* 輸入標籤的標籤：標籤會顯示在追蹤記錄中，
* 指定來源URL：此欄位僅供參考，可讓您指定追蹤的頁面（選擇性）。
* 如有需要，請輸入有效期間，
* 按一下&#x200B;**[!UICONTROL Generate]** HTML代碼。

然後複製產生的程式碼並將其貼到要追蹤的頁面中。

## 即時建立要追蹤的URL {#on-the-fly-creation-of-urls-to-be-tracked}

您可以將資訊新增至&#x200B;**tagid**&#x200B;引數的值，以立即建立網頁追蹤URL：

* 追蹤的頁面型別： WEB為&#39;w&#39;或TRANSACTION為&#39;t&#39;，
* 必須建立URL之資料夾的內部名稱。

這兩則資訊必須藉由新增字元&#39;|&#39;與追蹤頁面的識別碼串連：

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>**tagid**&#x200B;引數用作URL引數時，請記得將它編碼。

**範例**：建立交易型別的網頁追蹤URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
