---
title: 建立網頁追蹤標籤
seo-title: 建立網頁追蹤標籤
description: 建立網頁追蹤標籤
seo-description: null
page-status-flag: never-activated
uuid: c5599bdd-e6b8-4db4-b0ca-aaee2adc1919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 647ca037-4efb-4524-9642-11056d096aea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 建立網頁追蹤標籤{#creating-web-tracking-tags}

您要追蹤之網站的每個頁面都必須在您的Adobe Campaign平台中參考。 此引用可通過兩種方式執行：

1. 要追蹤之URL的手動定義、
1. 即時建立要追蹤的URL。

## 定義要在應用程式中追蹤的URL {#defining-the-urls-to-be-tracked-in-the-application}

此方法可讓您手動定義要追蹤的頁面，然後產生相關聯網頁追蹤標籤的範例。 此操作在客戶端控制台 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 的節點中定義。

![](assets/d_ncs_integration_webtracking_screen.png)

若要產生要插入頁面的HTML程式碼：

* 輸入標籤的標籤：會顯示在追蹤記錄中，
* 指定來源URL:此欄位僅供參考，可讓您指出追蹤的頁面（選用）、
* 如果需要，請輸入有效期，
* 按一 **[!UICONTROL Generate]** 下HTML程式碼。

然後複製產生的程式碼，並貼入要追蹤的頁面。

## 即時建立要追蹤的URL {#on-the-fly-creation-of-urls-to-be-tracked}

您可以借由新增資訊至 **tagid參數的值，即時建立網頁追蹤** URL:

* 追蹤的頁面類型：&#39;w&#39;代表WEB,&#39;t&#39;代表TRANSACTION,
* 必須建立URL的資料夾內部名稱。

這兩項資訊必須與追蹤頁面的識別碼串連，方法是新增字元&#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!CAUTION]
>
>當tagid參數用作URL參 **數時** ，請記得對其值進行編碼。

**範例**:建立交易類型網頁追蹤URL。

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
