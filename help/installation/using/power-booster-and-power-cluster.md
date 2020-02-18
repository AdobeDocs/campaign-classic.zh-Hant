---
title: 電源升壓器和電源群集
seo-title: 電源升壓器和電源群集
description: 電源升壓器和電源群集
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c25e2a4f2280cdcc61e0522f8235149410b5dacf

---


# 電源升壓器和電源群集{#power-booster-and-power-cluster}

## 概觀 {#overview}

Adobe Campaign提供兩組預先封裝的架構選項，讓您調整部署的尺寸：

* **Power Booster**

   此選項可支援與主要Adobe Campaign應用程式例項分離的單一額外執行例項。 專用執行實例可以遠程托管，也可以由第三方托管。 實作時，電子郵件執行、追蹤、鏡像頁面和彈回訊息會獨立於中央應用程式功能處理。

* **電源群集**

   此選項提供2到N個叢集執行例項的支援，這些執行例項與主要Adobe Campaign應用程式例項相對於特定應用程式的解耦。 叢集可由遠端、分散式部署中及第三方代管。 除了流程隔離的優點外，Adobe Campaign Power cluster選項還允許使用商品硬體進行冗餘和擴展策略，以簡化SLA或效能的演變。

![](assets/architectural_options_diagram.png)

## 符合資格的應用程式 {#eligible-applications}

Power Booster和Power cluster選項可用於以下應用程式：

* 行銷活動
* 傳送
* 訊息中心

## 建築推薦矩陣 {#matrix-of-architectural-recommendations}

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
   <td> 每月最多可收到約3千萬封電子郵件<br /> </td> 
   <td> 每月3000萬到1億封電子郵件<br /> </td> 
   <td> 每月超過1億封電子郵件<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易式訊息<br /> </td> 
   <td> 每執行伺服器每小時50,000次<br /> </td> 
   <td> 每執行伺服器每小時50,000次<br /> </td> 
   <td> 每執行伺服器每小時50,000次<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主資料庫的資料庫<br /> </td> 
   <td> 24/7，執行實例的維護窗口和下載時間除外<br /> </td> 
   <td> 24/7/365服務可能<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 資料集市可從公共網際網路訪問<br /> </td> 
   <td> 資料集市與面向網際網路的正面元件隔離<br /> </td> 
   <td> 資料集市與面向網際網路的正面元件隔離<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署範本<br /> </td> 
   <td> 所有功能都可在單一網站上（可在內部部署或在雲端）<br /> </td> 
   <td> 可在雲端執行的內部部署行銷<br /> </td> 
   <td> 在雲端執行內部部署行銷；在不同的情況下執行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建議 {#recommendations}

* 執行實例必須專用於服務。 您無法為尚未訂閱的服務安裝套件。 例如，如果您訂閱了消息中心服務的 **Power Booster** ( **Power Booster** )選項，則只能在專用執行實例 **[!UICONTROL Execution of transactional messages]** 上安裝軟體包。 請檢查您的授權合約。
* 由於專用例項（或叢集）是Adobe Campaign例項，因此建議與主例項相同。 For more on this, refer to [this document](../../production/using/foreword.md).
* 若要從資料庫／硬體元件的視點正確設定例項，請聯絡Adobe Campaign專業服務。

