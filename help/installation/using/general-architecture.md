---
title: 通用架構
seo-title: 通用架構
description: 通用架構
seo-description: null
page-status-flag: never-activated
uuid: 686bc660-2403-4bab-a4ea-9b872adf8fa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 7c28c179-eb18-437e-baf2-25829566c766
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 通用架構{#general-architecture}

典型的Adobe Campaign解決方案部署包含下列元件：

* **個人化用戶端環境**

   直覺式圖形介面，讓使用者可以在其中溝通及追蹤行銷優惠、建立促銷活動、審查及管理所有行銷活動、方案和計畫（包括電子郵件、工作流程和著陸頁面）、建立及管理客戶個人檔案，以及定義客戶受眾類型。

* **開發環境**

   伺服器端軟體，根據使用者介面中定義的規則和工作流程，透過選擇的通訊通道（包括電子郵件、簡訊、推播通知、直效郵件、網頁或社交）執行行銷宣傳。

* **資料庫容器**

   Adobe Campaign資料庫以關聯式資料庫技術為基礎，將所有客戶資訊、促銷活動元件、優惠和工作流程，以及促銷活動結果儲存在客戶資料庫容器中。

Adobe Campaign是以服務導向架構(SOA)為基礎，並包含數個功能模組。 這些模組可以部署在一個或多個電腦上，在單個或多個實例中，具體取決於可擴充性、可用性和服務隔離方面的限制。 因此，部署配置的範圍非常廣泛，可跨單台中央電腦到配置，包括跨多個站點的多台專用伺服器。

>[!NOTE]
>
>身為軟體供應商，我們指定相容的硬體和軟體基礎架構。 此處提供的硬體建議僅供參考，並以我們的經驗為基礎。 Adobe對任何根據此決定所做之決定概不負責。 它還取決於您的業務規則和做法，以及項目的重要性和所需的績效級別。

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>若未明確說明，則Adobe Campaign平台所有元件的安裝、更新和維護由代管元件的電腦管理員負責。 這包括實作Adobe Campaign應用程式的先決條件，以及遵守元件間的 [相容性矩陣](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 。

## 表現層 {#presentation-layer}

應用程式的存取方式視使用者需求而定：Rich client、Thin client或API整合。

* **Rich client**:應用程式的主要使用者介面是rich client，換言之，是原生應用程式(Windows)，僅與Adobe Campaign應用程式伺服器通訊，僅與標準網際網路通訊協定（SOAP、HTTP等）。 此主控台提供絕佳的使用便利性，讓您提高生產力，並且使用極少的頻寬（透過使用本機快取），而且易於部署。 此控制台可從網際網路瀏覽器部署、可自動更新，而且不需要任何特定網路組態，因為它只會產生HTTP(S)流量。
* **瘦客戶端**:應用程式的某些部分可使用HTML使用者介面，透過簡單的Web瀏覽器存取，包括報告模組、傳送核准階段、Distributed Marketing模組（中央／本機）的功能、例項監控等。 此模式可將Adobe Campaign功能納入內部網路或外部網路。
* **透過API進行整合**:在某些情況下，可使用透過SOAP通訊協定公開的Web Services API，從外部應用程式呼叫系統。

## 邏輯應用層 {#logical-application-layer}

Adobe Campaign是單一平台，其中包含不同的應用程式，可結合這些應用程式來建立開放且可擴充的架構。 Adobe Campaign平台是在有彈性的應用程式層上編寫，可輕鬆配置以符合公司的業務需求。 這從功能和技術角度適應了企業不斷增長的需求。 分佈式體系結構確保線性系統可擴充性從數千條消息擴展到數百萬條消息。

Adobe Campaign依賴一組可搭配運作的伺服器端程式。

主要流程有：

**應用程式伺服器** (nlserver web)

此程式透過網站服務API(SOAP - HTTP + XML)公開Adobe Campaign的完整功能。 此外，它還可動態產生用於HTML存取的網頁（報表、Web表格等）。 為此，此過程包括Apache Tomcat JSP伺服器。 這是控制台連接的過程。

**工作流引擎** (nlserver wfserver)

它會執行應用程式中定義的工作流程程式。

此外，它還可處理定期執行的技術工作流程，包括：

* 追蹤：恢復和合併跟蹤日誌。 它可讓您從重新導向伺服器擷取記錄檔，並建立報表模組所使用的匯總指示符。
* 清除：資料庫清除。 用於清除舊記錄並避免資料庫呈指數級增長。
* 帳單：自動傳送平台的活動報表（資料庫大小、行銷動作數等）。

**傳送伺服器** (nlserver mta)

Adobe Campaign具備原生的電子郵件廣播功能。 此進程充當SMTP郵件傳輸代理(MTA)。 它對郵件執行「一對一」個人化，並處理其實際傳遞。 它可使用傳送工作和處理自動重試。 此外，在啟用追蹤時，會自動取代URL，讓URL指向重新導向伺服器。

此程式可處理自訂和自動傳送給第三方路由器的SMS、傳真和直效郵件。

**重定向伺服器** (nlserver webmdl)

對於電子郵件，Adobe Campaign會自動處理開啟和點按追蹤（在網站層級進行交易追蹤的可能性更大）。 為此，會重寫包含在電子郵件訊息中的URL，以指向此模組，此模組會先註冊網際網路使用者的傳遞，再將其重新導向至所需的URL。

為保證最高可用性，此過程完全獨立於資料庫：其他伺服器程式僅使用SOAP呼叫(HTTP、HTTP(S)和XML)與其通訊。 技術上，此功能是在HTTP伺服器的擴充模組（IIS中的ISAPI擴充功能，或DSO Apache模組等）中實作而且僅適用於Windows。

還提供其他技術程式：

**管理彈回電子郵件** (nlserver inMail)

此過程使您能夠從配置為接收在發送失敗時返回的已跳回郵件的郵箱中自動獲取電子郵件。 然後，這些訊息會進行規則型處理，以判斷未傳送（未知收件者、超出配額等）的原因和更新資料庫中的傳送狀態。

所有這些操作都是完全自動和預配置的。

**SMS傳送狀態** (nlserver sms)

此過程輪詢SMS路由器以收集進度狀態並更新資料庫。

**寫入日誌消息** (nlserver syslogd)

此技術過程捕獲其他進程生成的日誌消息和跟蹤，並將其寫入硬碟。 這樣，在出現問題時，就可以獲得足夠的診斷資訊。

**寫入追蹤記錄** (nlserver trackinglogd)

此進程將重定向進程生成的跟蹤日誌保存到磁碟。

**寫入入站事件** (nlserver interactiond)

此程式可確保在「交互」框架內將傳入事件記錄到磁碟。

**監控模組** （nlserver監視程式）

此技術程式是產生其他程式的主程式。 此外，它還會監控並在發生意外時自動重新啟動它們，從而維持最大的系統正常運行時間。

**統計伺服器** (nlserver stat)

此過程維護有關連接數、發送給每個郵件伺服器的郵件數以及其限制（每小時和／或連接的同時連接數最多）的統計資訊。 如果多個實例或電腦共用相同的公共IP地址，它還允許您聯合這些實例或電腦。

>[!NOTE]
>
>本檔案提供Adobe Campaign模組的完整 [清單](../../production/using/operating-principle.md)。

## 持久層 {#persistence-layer}

資料庫是做為永續性層，並包含幾乎所有由Adobe Campaign管理的資訊。 這包括功能資料（描述檔、訂閱、內容等）、技術資料（傳送工作和記錄檔、追蹤記錄檔等）和工作資料（購買、銷售機會）。

資料庫的可靠性至關重要，因為大部份的Adobe Campaign元件都需要存取資料庫才能執行其工作（重新導向模組除外）。

該平台預先定義了以營銷為中心的資料集市，或者可以使用任何主要的關係資料庫管理系統(RDBMS)輕鬆地置於現有資料集市和模式之上。 資料集市中的所有資料都可由Adobe Campaign平台透過從Adobe Campaign到資料庫的SQL呼叫存取。 Adobe Campaign也提供完整的摘取轉換與載入(ETL)工具，以執行資料匯入與匯出至系統或匯出系統。
