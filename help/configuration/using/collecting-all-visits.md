---
product: campaign
title: 收集所有瀏覽次數
description: 收集所有瀏覽次數
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 收集所有瀏覽次數{#collecting-all-visits}

![](../../assets/v7-only.svg)

Adobe Campaign提供的Web跟蹤模組允許您收集收件人在郵件點擊後在站點跟蹤上下文中對站點某些頁面的訪問。

但是，您可以配置平台，以便它收集平台已知用戶對帶有Web跟蹤標籤的頁面的所有訪問。

該平台已知的用戶是已被遞送鎖定並且已至少按一下一次接收的消息的接收者。 永久Cookie用於標識此收件人。

>[!IMPORTANT]
>
>Adobe Campaign平台不打算用作網站跟蹤工具，而不是在留言點擊後訪問網站。 啟用此選項後，可能會導致伺服器所在的電腦（重定向、應用程式和資料庫）上資源的使用率非常高。 建議您確保硬體體系結構能夠支援此負載，並避免在最頻繁訪問的頁面（如首頁）中放置Web跟蹤標籤。

## 伺服器配置 {#server-configuration}

通過使某些元素超載配置伺服器 **serverConf.xml** 的子菜單。 這些檔案保存在 **會議** 的子目錄。

### 重定向伺服器 {#redirection-server}

對於重定向伺服器，設定 **跟蹤Web訪問者** 屬性 **重定向** 元素 **真**。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 配置預設匹配市場活動 {#configuring-a-default-matching-campaign}

要通過客戶端控制台查看跟蹤資訊，您必須：

* 建立 **虛擬送貨** （傳遞映射必須與目標架構的映射相同）,
* 輸入 **內部名稱** 這次交貨 **NmsTracking_WebTrackingDelivery** 的雙曲餘切值。

在電子郵件中按一下之後不直接查看的所有站點跟蹤資訊都可以在建立的虛擬傳遞中查看。
