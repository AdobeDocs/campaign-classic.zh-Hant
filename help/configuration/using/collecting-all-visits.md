---
solution: Campaign Classic
product: campaign
title: 收集所有瀏覽
description: 收集所有瀏覽
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---


# 收集所有瀏覽{#collecting-all-visits}

Adobe Campaign提供的網頁追蹤模組可讓您收集收件者在訊息中按一下後，在網站追蹤內容中對網站的特定頁面所執行的瀏覽。

不過，您可以設定平台，讓平台透過平台已知的使用者使用網頁追蹤標籤收集所有頁面的瀏覽。

該平台已知的用戶是已被遞送鎖定並且已點擊接收消息至少一次的接收者。 永久Cookie可用來識別此收件者。

>[!IMPORTANT]
>
>Adobe Campaign平台不適用於在訊息中按一下之後造訪網站的上下文以外，做為網站追蹤工具。 啟用此選項後，可能會在您的伺服器所在的電腦上（重新導向、應用程式和資料庫），造成資源的高使用率。 建議您確保硬體架構可支援此載入，並避免將網頁追蹤標籤放置在最常造訪的頁面（例如首頁）中。

## 伺服器配置{#server-configuration}

通過超載&#x200B;**serverConf.xml**&#x200B;檔案的某些元素來配置伺服器。 這些檔案會儲存在Adobe Campaign安裝目錄的&#x200B;**conf**&#x200B;子目錄中。

### 重定向伺服器{#redirection-server}

對於重定向伺服器，將&#x200B;**redirection**&#x200B;元素的&#x200B;**trackWebVisitors**&#x200B;屬性設定為&#x200B;**true**。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 設定預設符合的促銷活動{#configuring-a-default-matching-campaign}

若要透過用戶端主控台檢視追蹤資訊，您必須：

* 建立&#x200B;**虛擬傳送**（傳送映射必須與目標模式的映射相同）,
* 在&#x200B;**NmsTracking_WebTrackingDelivery**&#x200B;選項中輸入此傳送的&#x200B;**內部名稱**。

並非直接在電子郵件中點按後顯示的所有網站追蹤資訊，都可以在建立的虛擬傳送中檢視。
