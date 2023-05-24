---
product: campaign
title: 網路設定
description: 瞭解系統通訊指南
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



## 處理程式之間的通訊 {#communication-between-processes}

應用程式的某些程式需要與他人通訊或存取區域網路和網際網路。 這表示這些處理程式需要開啟某些TCP連線埠。

使用內嵌式Apache Tomcat連線埠作為優先順序（預設為8080），在Adobe Campaign平台的各種應用程式伺服器之間進行內部通訊。

### 傳遞伺服器 {#delivery-server}

對於傳遞伺服器(**nlserver mta**)，則必須開啟下列連線埠：

<table> 
 <tbody> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> 隨處<br /> </td> 
   <td> 用於電子郵件廣播的SMTP流量。<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp （網域）<br /> </td> 
   <td> DNS伺服器<br /> </td> 
   <td> dns查詢。<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp （預設連線埠）<br /> </td> 
   <td> 簡訊閘道<br /> </td> 
   <td> 用來傳送SMS流量至NetSize SMS路由器[選項]。<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 統計值伺服器<br /> </td> 
   <td> 存取統計資料伺服器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 傳入郵件 {#inbound-mail}

針對傳入郵件復原程式(**nlserver inMail**)，則必須開啟下列連線埠：

<table> 
 <tbody> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> 內部郵件伺服器<br /> </td> 
   <td> 擷取退回訊息的POP3流量。<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> 內部郵件伺服器<br /> </td> 
   <td> 用於傳送未由預先定義規則自動處理的剩餘退回訊息的SMTP流量。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 應用程式伺服器 {#application-server}

針對應用程式伺服器(**nlserver web**)，則必須開啟下列連線埠：

<table> 
 <tbody> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> 隨處<br /> </td> 
   <td> HTTP或HTTPS流量（包括用於傳遞能力選件）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

當Adobe Campaign平台的多個應用程式伺服器需要彼此通訊時，我們建議使用Apache Tomcat伺服器的連線埠（預設為8080），而不是使用執行重新導向模組整合之Web伺服器的HTTP連線埠的連線埠。 這表示這些伺服器之間的連線埠必須開啟。

### 簡訊傳遞狀態 {#sms-delivery-status}

若要追蹤簡訊傳遞(**nlserver sms**)，則必須開啟下列連線埠：

<table> 
 <tbody> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp （預設連線埠）<br /> </td> 
   <td> 簡訊閘道<br /> </td> 
   <td> 查詢由NetSize SMS閘道[選項]管理的傳遞佇列狀態。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 豐富型使用者端 {#rich-client}

適用於Adobe Campaign rich client (**nlclient**)，則必須開啟下列連線埠：

<table> 
 <tbody> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> 目的地<br /> </td> 
   <td> 評論<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> 應用程式伺服器<br /> </td> 
   <td> SOAP流量(HTTP)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 資料庫存取 {#database-access}

使用資料庫的所有元件都必須能夠連線到資料庫。 大多數元件都是如此，除了可單獨運作的重新導向伺服器，以及只使用HTTP （或HTTPS）與應用程式伺服器通訊的精簡Win32使用者端以外。

預設連線埠如下：

<table> 
 <tbody> 
  <tr> 
   <td> 資料庫類型<br /> </td> 
   <td> 連線埠（預設）<br /> </td> 
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

## 外部存取 {#external-access}

此外，某些元件必須可從公用網際網路存取，以便檢視直接從Adobe Campaign執行的電子郵件行銷活動。 這表示某些連線埠必須為元件開啟。

### 重新導向伺服器 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 接聽連線埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> 隨處。 每次點按追蹤的連結時，就會在伺服器上產生HTTP要求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 外部Web伺服器 {#external-web-server}

此伺服器會託管網路表單、映象頁面等。 需要開啟下列連線埠：

<table> 
 <tbody> 
  <tr> 
   <td> 接聽連線埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> 隨處。 直接從Adobe Campaign平台管理網路表單，或使用映象頁面時，此為必要專案。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 內部應用程式伺服器（網頁） {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> 接聽連線埠<br /> </td> 
   <td> 位置<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> 執行精簡型使用者端或豐富型使用者端的所有電腦。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 與Adobe Experience Manager整合 {#integration-with-adobe-experience-manager}

如果安裝是「內部部署」，Adobe Campaign與Adobe Experience Manager之間的整合需要開啟多個連線埠。 如需設定此整合的詳細資訊，請參閱 [詳細檔案](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> 接聽連線埠<br /> </td> 
   <td> 說明<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM與Adobe Campaign的連線<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign與AEM「編寫」和「發佈」執行個體的連線。 視您的AEM設定而定，要開啟的連線埠可能與預設的連線埠不同。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 頻寬 {#bandwidth}

要考慮的網路設定的另一個關鍵引數。 電子郵件幾乎總是對外傳送，而且在電子郵件廣播期間會有許多需求。 以下是一些根據我們經驗進行的設定範例：

* 每小時10,000封電子郵件為1 Mb/s （平均大小為30 Kb）
* 每小時100,000封電子郵件為8到10 Mb/s （平均大小為30 Kb）

如果您的頻寬有限制，則可排程行銷活動，以便在需求較低時於夜間執行。
