---
product: campaign
title: 收集所有瀏覽次數
description: 收集所有瀏覽次數
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 收集所有瀏覽次數{#collecting-all-visits}

Adobe Campaign提供的網頁追蹤模組可讓您收集收件者在追蹤網站時對網站特定頁面的造訪，該收件者會在訊息中按一下後於追蹤網站內容中執行。

不過，您可以設定您的平台，讓平台已知使用者透過網頁追蹤標籤收集所有頁面的造訪次數。

平台已知的使用者是已被傳遞鎖定，且已點按至少一次收到訊息的收件者。 永久Cookie可用來識別此收件者。

>[!IMPORTANT]
>
>除了在訊息中按一下後造訪網站的上下文以外，Adobe Campaign平台並非用作網站追蹤工具。 啟用此選項後，可能會在托管伺服器的電腦上（重定向、應用程式和資料庫）導致資源的高使用率。 建議您確保硬體架構可支援此載入，並避免將網頁追蹤標籤放在最常造訪的頁面（例如首頁）中。

## 伺服器設定 {#server-configuration}

伺服器的設定方式，是透過 **serverConf.xml** 檔案。 這些檔案會儲存在 **conf** Adobe Campaign安裝目錄的子目錄。

### 重定向伺服器 {#redirection-server}

對於重定向伺服器，設定 **trackWebVisitors** 屬性 **重定向** 元素 **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 設定預設的相符促銷活動 {#configuring-a-default-matching-campaign}

若要透過用戶端主控台檢視追蹤資訊，您必須：

* 建立 **虛擬傳送** （傳送對應必須與目標架構的對應相同）,
* 輸入 **內部名稱** 在 **NmsTracking_WebTrackingDelivery** 選項。

並非直接在電子郵件中點按後顯示的所有網站追蹤資訊，都可在建立的虛擬傳送中檢視。
