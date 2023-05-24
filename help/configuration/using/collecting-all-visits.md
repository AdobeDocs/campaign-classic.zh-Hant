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

Adobe Campaign提供的網路追蹤模組可讓您收集收件者在訊息中點按後，在網站追蹤的情境下，對網站特定頁面執行的造訪。

不過，您可以設定平台，使其收集平台已知使用者對具有網頁追蹤標籤之頁面的所有造訪。

平台已知的使用者是指已設為傳送目標，且已至少點按一次已接收訊息的收件者。 永久性Cookie可用來識別此收件者。

>[!IMPORTANT]
>
>Adobe Campaign平台不適用作為網站追蹤工具，而不僅限於在訊息中點按後造訪網站的環境。 啟用此選項時，可能會導致託管伺服器之電腦上的資源使用率非常高（重新導向、應用程式和資料庫）。 建議您確保硬體架構可支援此載入，並避免將Web追蹤標籤放在最常造訪的頁面（例如首頁）中。

## 伺服器設定 {#server-configuration}

伺服器的設定方式為多載某些元素 **serverConf.xml** 檔案。 這些檔案會儲存在 **conf** Adobe Campaign安裝目錄的子目錄。

### 重新導向伺服器 {#redirection-server}

對於重新導向伺服器，設定 **trackWebVisitors** 的屬性 **重新導向** 元素至 **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 設定預設相符的行銷活動 {#configuring-a-default-matching-campaign}

若要透過使用者端主控台檢視追蹤資訊，您必須：

* 建立 **虛擬傳遞** （傳遞對應必須與目標結構描述的對應相同），
* 輸入 **內部名稱** 此傳遞在 **NmsTracking_WebTrackingDelivery** 選項。

所有並非直接在電子郵件中點選之後的網站追蹤資訊，都可以在建立的虛擬傳遞中檢視。
