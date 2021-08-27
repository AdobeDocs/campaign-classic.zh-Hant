---
product: campaign
title: 收集所有瀏覽次數
description: 收集所有瀏覽次數
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 收集所有瀏覽次數{#collecting-all-visits}

![](../../assets/v7-only.svg)

Adobe Campaign提供的網頁追蹤模組可讓您收集收件者在追蹤網站時對網站特定頁面的造訪，該收件者會在訊息中按一下後於追蹤網站內容中執行。

不過，您可以設定您的平台，讓平台已知使用者透過網頁追蹤標籤收集所有頁面的造訪次數。

平台已知的使用者是已被傳遞鎖定，且已點按至少一次收到訊息的收件者。 永久Cookie可用來識別此收件者。

>[!IMPORTANT]
>
>除了在訊息中按一下後造訪網站的上下文以外，Adobe Campaign平台並非用作網站追蹤工具。 啟用此選項後，可能會在托管伺服器的電腦上（重定向、應用程式和資料庫）導致資源的高使用率。 建議您確保硬體架構可支援此載入，並避免將網頁追蹤標籤放在最常造訪的頁面（例如首頁）中。

## 伺服器配置 {#server-configuration}

伺服器是透過超載&#x200B;**serverConf.xml**&#x200B;檔案的某些元素來設定。 這些檔案儲存在Adobe Campaign安裝目錄的&#x200B;**conf**&#x200B;子目錄中。

### 重定向伺服器 {#redirection-server}

對於重定向伺服器，將&#x200B;**redirection**&#x200B;元素的&#x200B;**trackWebVisitors**&#x200B;屬性設定為&#x200B;**true**。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 設定預設的相符促銷活動 {#configuring-a-default-matching-campaign}

若要透過用戶端主控台檢視追蹤資訊，您必須：

* 建立&#x200B;**虛擬傳送**（傳送對應必須與目標架構的對應相同）,
* 在&#x200B;**NmsTracking_WebTrackingDelivery**&#x200B;選項中輸入此傳送的&#x200B;**內部名稱**。

並非直接在電子郵件中的點按後顯示的所有網站追蹤資訊，都可在建立的虛擬傳送中檢視。
