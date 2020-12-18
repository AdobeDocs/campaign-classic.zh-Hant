---
solution: Campaign Classic
product: campaign
title: Power Booster 與 Power Cluster
description: Power Booster 與 Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---


# Power Booster 與 Power Cluster{#power-booster-and-power-cluster}

## 概觀 {#overview}

Adobe Campaign提供兩組預先封裝的架構選項，讓您調整部署的尺寸：

* **Power Booster**

   此選項可支援與主要Adobe Campaign應用程式例項分離的單一額外執行例項。 專用執行實例可以遠程托管，也可以由第三方托管。 實作時，電子郵件執行、追蹤、鏡像頁面和彈回訊息會獨立於中央應用程式功能處理。

* **電源群集**

   此選項提供2到N個叢集執行例項的支援，這些執行例項與主要Adobe Campaign應用程式例項相對於特定應用程式的解耦。 叢集可由遠端、分散式部署中及第三方代管。 除了流程隔離的優點外，Adobe Campaign Power Cluster選項還允許使用商品硬體進行冗餘和擴展策略，以簡化SLA或效能的演變。

![](assets/architectural_options_diagram.png)

## 符合資格的應用程式{#eligible-applications}

Power Booster和Power Cluster選項可用於以下應用程式：

* Campaign
* 傳送
* 訊息中心

## 建築建議矩陣{#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>標準架構</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>電源群集</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件促銷活動和對外互動<br /> </td> 
   <td> 每月最多約3000萬封電子郵件<br /> </td> 
   <td> 每月3000萬到1億封電子郵件<br /> </td> 
   <td> 每月超過1億封電子郵件<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易式訊息<br /> </td> 
   <td> 每個執行伺服器每小時50,000<br /> </td> 
   <td> 每個執行伺服器每小時50,000<br /> </td> 
   <td> 每個執行伺服器每小時50,000<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主資料庫的資料庫<br /> </td> 
   <td> 24/7，執行實例的維護窗口和下載時間<br />除外 </td> 
   <td> 24/7/365服務可能<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 資料集市可從公共網際網路訪問<br /> </td> 
   <td> 資料集市與正面、面向網際網路的元件隔離<br /> </td> 
   <td> 資料集市與正面、面向網際網路的元件隔離<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署模板<br /> </td> 
   <td> 所有內容都在一個網站上（可在內部部署或在雲端）<br /> </td> 
   <td> 可在雲端執行的內部部署行銷<br /> </td> 
   <td> 在雲端執行內部部署行銷；可能執行的不同格點<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建議 {#recommendations}

* 執行實例必須專用於服務。 您無法為尚未訂閱的服務安裝套件。 例如，如果您訂閱&#x200B;**消息中心**&#x200B;服務的&#x200B;**Power Booster**&#x200B;選項，則只能在專用執行實例上安裝&#x200B;**[!UICONTROL Execution of transactional messages]**&#x200B;軟體包。 請檢查您的授權合約。
* 由於專用例項（或叢集）是Adobe Campaign例項，因此建議與主例項相同。 有關詳細資訊，請參閱[本文檔](../../production/using/foreword.md)。
* 若要從資料庫／硬體元件的視點正確設定例項，請聯絡Adobe Campaign專業服務。

