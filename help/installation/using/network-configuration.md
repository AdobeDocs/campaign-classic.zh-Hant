---
product: campaign
title: 網路設定
description: 了解系統通信指南
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---

# 網路設定{#network-configuration}

![](../../assets/v7-only.svg)

## 進程之間的通信 {#communication-between-processes}

應用程式的某些進程需要與他人通信或訪問區域網路和網際網路。 這意味著需要為這些進程開啟某些TCP埠。

將內嵌的Apache Tomcat埠作為優先順序（預設為8080），用於Adobe Campaign平台的各種應用程式伺服器之間的內部通信。

### 傳送伺服器 {#delivery-server}

對於傳送伺服器(**nlserver mta**)，必須開啟以下埠：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目標<br /> </td> 
   <td> 注釋<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> 電子郵件廣播的SMTP通信。<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp（域）<br /> </td> 
   <td> DNS伺服器<br /> </td> 
   <td> DNS查詢。<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（預設埠）<br /> </td> 
   <td> SMS網關<br /> </td> 
   <td> 用於將SMS通信發送到NetSize SMS路由器[option]。<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 統計伺服器<br /> </td> 
   <td> 訪問統計伺服器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 傳入郵件 {#inbound-mail}

對於入站郵件恢復進程(**nlserver inMail**)，必須開啟以下埠：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目標<br /> </td> 
   <td> 注釋<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp(pop3)<br /> </td> 
   <td> 內部郵件伺服器<br /> </td> 
   <td> POP3流量以提取退信。<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 內部郵件伺服器<br /> </td> 
   <td> SMTP流量，用於發送未由預先定義的規則自動處理的剩餘退信。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 應用程式伺服器 {#application-server}

對於應用程式伺服器(**nlserver web**)，必須開啟以下埠：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目標<br /> </td> 
   <td> 注釋<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp(http)<br /> 443/tcp(https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> HTTP或HTTPS流量（包括傳遞能力選件）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

當Adobe Campaign平台的多個應用程式伺服器需要彼此通訊時，建議使用Apache Tomcat伺服器的埠(預設為：8080)，而非執行重定向模組整合的Web伺服器的HTTP埠。 這表示這些伺服器之間需要開啟埠。

### 簡訊傳送狀態 {#sms-delivery-status}

若要追蹤SMS傳送(**nlserver sms**)，必須開啟下列連接埠：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目標<br /> </td> 
   <td> 注釋<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（預設埠）<br /> </td> 
   <td> SMS網關<br /> </td> 
   <td> 查詢由NetSize SMS網關[option]管理的傳送隊列狀態。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 富客戶端 {#rich-client}

對於Adobe Campaign rich client(**nlclient**)，必須開啟以下埠：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目標<br /> </td> 
   <td> 注釋<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p>443/tcp(https)</p><br /> </td> 
   <td> 應用程式伺服器<br /> </td> 
   <td> SOAP流量(HTTP)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 資料庫存取 {#database-access}

使用資料庫的所有元件都必須能夠連接到該資料庫。 大多數元件都是這樣，但重定向伺服器可單獨工作除外，瘦Win32客戶端僅使用HTTP（或HTTPS）與應用程式伺服器通信。

預設埠如下：

<table> 
 <tbody> 
  <tr> 
   <td> 資料庫類型<br /> </td> 
   <td> 埠（預設）<br /> </td> 
   <td> 目標<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> 資料庫伺服器<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 外部訪問 {#external-access}

此外，某些元件必須可從公開網際網路存取，才能檢視直接從Adobe Campaign執行的電子郵件促銷活動。 這表示某些埠需要為元件開啟。

### 重定向伺服器 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 偵聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 隨處皆可。 每個點擊追蹤的連結都會在伺服器上產生HTTP要求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 外部Web伺服器 {#external-web-server}

此伺服器托管Web表單、鏡像頁面等。 需要開啟以下埠：

<table> 
 <tbody> 
  <tr> 
   <td> 偵聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 隨處皆可。 直接從Adobe Campaign平台管理Web表單或使用鏡像頁面時的必要條件。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 內部應用程式伺服器(Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> 偵聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 執行瘦客戶機或富客戶機的所有電腦。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 與Adobe Experience Manager整合 {#integration-with-adobe-experience-manager}

如果安裝為「內部部署」，Adobe Campaign和Adobe Experience Manager之間的整合需要開啟數個埠。 如需設定此整合的詳細資訊，請參閱[詳細檔案](../../integrations/using/about-adobe-experience-manager.md)。

<table> 
 <tbody> 
  <tr> 
   <td> 偵聽埠<br /> </td> 
   <td> 說明<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM連線至Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign連線至AEM「編寫」和「發佈」執行個體。 要開啟的埠可能與預設埠不同，具體取決於您的AEM配置。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 頻寬 {#bandwidth}

要考慮的網路配置的另一個關鍵參數。 電子郵件廣播中，它幾乎總是出站，而且需求很大。 以下是根據我們經驗進行的幾個設定範例：

* 每小時10,000封電子郵件為1 Mb/s（平均大小為30 Kb）
* 每小時100,000封電子郵件為8至10 Mb/s（平均大小30 Kb）

如果您在頻寬方面有限制，則可以排程在需求較低的夜晚執行促銷活動。
