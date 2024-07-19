---
product: campaign
title: 收集所有瀏覽次數
description: 收集所有瀏覽次數
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 3%

---

# 收集所有瀏覽次數{#collecting-all-visits}

Adobe Campaign提供的網路追蹤模組可讓您在訊息中按一下後，收集收件者針對網站追蹤內容所執行之網站特定頁面的造訪。

不過，您可以設定平台，使其收集平台已知使用者對具有網頁追蹤標籤之頁面的所有造訪。

平台已知的使用者是指已設為傳送目標，且已按一下已接收訊息至少一次的收件者。 永久性Cookie可用來識別此收件者。

>[!IMPORTANT]
>
>Adobe Campaign平台的用途不在於在訊息中按一下後造訪網站，而僅作為網站追蹤工具。 啟用此選項時，可能會導致伺服器主機上的資源使用率非常高（重新導向、應用程式和資料庫）。 建議您確保硬體架構可支援此載入作業，並避免將網頁追蹤標籤放在最常造訪的頁面（例如首頁）中。

## 伺服器設定 {#server-configuration}

伺服器是透過超載&#x200B;**serverConf.xml**&#x200B;檔案的特定元素來設定。 這些檔案儲存在Adobe Campaign安裝目錄的&#x200B;**conf**&#x200B;子目錄中。

### 重新導向伺服器 {#redirection-server}

對於重新導向伺服器，將&#x200B;**重新導向**&#x200B;專案的&#x200B;**trackWebVisitors**&#x200B;屬性設定為&#x200B;**true**。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 設定預設的相符行銷活動 {#configuring-a-default-matching-campaign}

若要透過使用者端主控台檢視追蹤資訊，您必須：

* 建立&#x200B;**虛擬傳遞** （傳遞對應必須與目標結構描述的對應相同），
* 在&#x200B;**NmsTracking_WebTrackingDelivery**&#x200B;選項中輸入此傳遞的&#x200B;**內部名稱**。

所有並非直接在電子郵件中點按後顯示的網站追蹤資訊，都可以在建立的虛擬傳遞中檢視。
