---
title: 網路配置
seo-title: 網路配置
description: 網路配置
seo-description: null
page-status-flag: never-activated
uuid: 17357170-7440-4603-bea6-2e4b9086ae72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 639d2f42-e397-4694-942c-b2b8ad94ce9c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 網路配置{#network-configuration}

## 進程間的通信 {#communication-between-processes}

應用程式的某些程式需要與其他人通訊或存取LAN和網際網路。 這意味著某些TCP埠需要為這些進程開啟。

使用內嵌的Apache Tomcat埠作為優先順序（預設為8080），在Adobe Campaign平台的各種應用程式伺服器之間進行內部通訊。

### 傳送伺服器 {#delivery-server}

對於傳送伺服器(**nlserver mta**)，必須開啟下列埠：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目標<br /> </td> 
   <td> 注釋<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 隨處皆可<br /> </td> 
   <td> 電子郵件廣播的SMTP通信。<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp（域）<br /> </td> 
   <td> DNS伺服器<br /> </td> 
   <td> DNS查詢。<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（預設埠）<br /> </td> 
   <td> SMS閘道<br /> </td> 
   <td> 用於將SMS通信發送到NetSize SMS路由器[選項]。<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 統計伺服器<br /> </td> 
   <td> 訪問統計伺服器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 入站郵件 {#inbound-mail}

對於入站郵件恢復過程(**nlserver inMail**)，必須開啟以下埠：

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
   <td> POP3流量，以擷取反彈訊息。<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 內部郵件伺服器<br /> </td> 
   <td> SMTP流量，用於發送未由預定義規則自動處理的剩餘彈回消息。<br /> </td> 
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
   <td> 隨處皆可<br /> </td> 
   <td> HTTP或HTTPS流量（包括可傳遞性選件）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

當Adobe Campaign平台的數個應用程式伺服器需要彼此通訊時，建議使用Apache Tomcat伺服器的連接埠(預設為：8080)，而非執行重定向模組整合的Web伺服器的HTTP埠。 這表示這些伺服器之間需要開啟埠。

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
   <td> SMS閘道<br /> </td> 
   <td> 查詢由NetSize SMS網關[選項]管理的發送隊列狀態。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Rich client {#rich-client}

對於Adobe Campaign rich client(**nlclient**)，必須開啟下列埠：

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

使用資料庫的所有元件都必須能夠連接到它。 大多數元件都是這樣，但重定向伺服器（可獨立工作）和瘦Win32客戶端(僅使用HTTP（或HTTPS）與應用程式伺服器通信)除外。

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

## 外部存取 {#external-access}

此外，某些元件必須可從公共網際網路存取，才能檢視直接從Adobe Campaign執行的電子郵件促銷活動。 這表示某些埠需要為元件開啟。

### 重定向伺服器 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 監聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 隨處皆可。 每次點按追蹤的連結時，都會在伺服器上產生HTTP要求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 外部Web伺服器 {#external-web-server}

此伺服器托管Web表單、鏡像頁等。 需要開啟以下埠：

<table> 
 <tbody> 
  <tr> 
   <td> 監聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 隨處皆可。 從Adobe Campaign平台直接管理Web表單或使用鏡像頁面時的必要性。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 內部應用程式伺服器(Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> 監聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 執行瘦客戶機或rich client的所有電腦。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 與Adobe Experience Manager整合 {#integration-with-adobe-experience-manager}

如果安裝是「內部部署」，則Adobe Campaign與Adobe Experience manager之間的整合需要開啟數個埠。 如需設定此整合的詳細資訊，請參閱詳細 [的檔案](../../integrations/using/about-adobe-experience-manager.md)。

<table> 
 <tbody> 
  <tr> 
   <td> 監聽埠<br /> </td> 
   <td> 說明<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM與Adobe Campaign的連線<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign與AEM的「編寫」和「發佈」例項的連線。 要開啟的埠可能與預設埠不同，視您的AEM設定而定。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 頻寬 {#bandwidth}

要考慮的網路配置的另一個關鍵參數。 在電子郵件廣播中，它幾乎總是對外發送，而且有很多需求。 以下是一些基於我們經驗的配置示例：

* 每小時10,000封電子郵件需要1 Mb/s（平均大小為30 Kb）
* 每小時100,000封電子郵件需8至10 Mb/s（平均大小為30 Kb）

如果您在頻寬方面有限制，則可排程促銷活動在需求較低的夜晚執行。
