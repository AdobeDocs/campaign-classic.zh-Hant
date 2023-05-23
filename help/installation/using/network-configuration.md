---
product: campaign
title: 網路設定
description: 學習系統通信指南
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 5%

---

# 網路設定{#network-configuration}



## 進程之間的通信 {#communication-between-processes}

應用程式的某些進程需要與他人通信或訪問區域網路和網際網路。 這意味著需要為這些進程開啟某些TCP埠。

使用嵌入式Apache Tomcat埠作為優先順序（預設為8080），在Adobe Campaign平台的各種應用程式伺服器之間進行內部通信。

### 傳遞伺服器 {#delivery-server}

對於傳遞伺服器(**nlserver mta**)，下列埠必須開啟：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 隨處<br /> </td> 
   <td> 用於電子郵件廣播的SMTP通信。<br /> </td> 
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

### 入站郵件 {#inbound-mail}

對於入站郵件恢復進程(**nlserver inMail**)，下列埠必須開啟：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp(pop3)<br /> </td> 
   <td> 內部郵件伺服器<br /> </td> 
   <td> POP3通信量，用於接收退回消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 內部郵件伺服器<br /> </td> 
   <td> 發送未由預定義規則自動處理的剩餘彈回消息的SMTP通信。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 應用程式伺服器 {#application-server}

對於應用程式伺服器(**nlserver web**)，下列埠必須開啟：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp(http)<br /> 443/tcp(https)<br /> </td> 
   <td> 隨處<br /> </td> 
   <td> HTTP或HTTPS通信（包括提供服務）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

當Adobe Campaign平台的多個應用程式伺服器需要相互通信時，建議使用Apache Tomcat伺服器的埠(預設情況下：8080)，而不是Web伺服器的HTTP埠，該HTTP埠與重定向模組進行整合。 這意味著需要在這些伺服器之間開啟埠。

### SMS傳遞狀態 {#sms-delivery-status}

跟蹤SMS遞送(**nlserver sms**)，下列埠必須開啟：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp（預設埠）<br /> </td> 
   <td> SMS網關<br /> </td> 
   <td> 查詢由NetSize SMS網關[選項]管理的傳遞隊列狀態。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 富客戶端 {#rich-client}

對於Adobe Campaign富客戶(**nlclient**)，下列埠必須開啟：

<table> 
 <tbody> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p>443/tcp(https)</p><br /> </td> 
   <td> 應用程式伺服器<br /> </td> 
   <td> SOAP通信(HTTP)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 資料庫訪問 {#database-access}

使用資料庫的所有元件都必須能夠連接到它。 這適用於大多數元件，但重定向伺服器和瘦Win32客戶端除外，後者僅使用HTTP（或HTTPS）與應用程式伺服器通信。

預設埠如下：

<table> 
 <tbody> 
  <tr> 
   <td> 資料庫類型<br /> </td> 
   <td> 埠（預設）<br /> </td> 
   <td> 目的地<br /> </td> 
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

此外，某些元件必須可從公共網際網路訪問，以便能夠查看直接從Adobe Campaign執行的電子郵件活動。 這意味著某些埠需要為元件開啟。

### 重定向伺服器 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 偵聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 隨便哪。 每次按一下跟蹤的連結都會在伺服器上生成HTTP請求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 外部Web伺服器 {#external-web-server}

此伺服器承載Web表單、鏡像頁等。 需要開啟以下埠：

<table> 
 <tbody> 
  <tr> 
   <td> 偵聽埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 隨便哪。 從Adobe Campaign平台直接管理Web表單或使用鏡像頁時是必需的。<br /> </td> 
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
   <td> 執行瘦客戶端或富客戶端的所有電腦。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 與Adobe Experience Manager {#integration-with-adobe-experience-manager}

Adobe Campaign和Adobe Experience Manager之間的整合需要在安裝「內部」的情況下開放幾個港口。 有關配置此整合的詳細資訊，請參閱 [詳細文檔](../../integrations/using/about-adobe-experience-manager.md)。

<table> 
 <tbody> 
  <tr> 
   <td> 偵聽埠<br /> </td> 
   <td> 說明<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEMAdobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign與AEM"創作"和"發佈"實例的連接。 要開啟的埠可能與預設埠不同，具體取決於您的AEM配置。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 頻寬 {#bandwidth}

要考慮的網路配置的另一個關鍵參數。 它幾乎總是在外出，在電子郵件廣播中非常有需求。 下面是一些基於我們經驗的配置示例：

* 每小時10,000封電子郵件（平均大小為30 Kb）為1 Mb/s
* 每小時100,000封電子郵件（平均大小為30 Kb）為8到10 Mb/s

如果您在頻寬方面有限制，則可以計畫在需求較低的夜間運行市場活動。
