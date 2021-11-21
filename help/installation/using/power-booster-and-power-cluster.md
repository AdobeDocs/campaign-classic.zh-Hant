---
product: campaign
title: Power Booster 與 Power Cluster
description: Power Booster 與 Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# Power Booster 與 Power Cluster{#power-booster-and-power-cluster}

![](../../assets/v7-only.svg)

## 概覽 {#overview}

Adobe Campaign提供兩組預先封裝的架構選項，讓您調整部署的尺寸：

* **Power Booster**

   此選項支援與主要Adobe Campaign應用程式例項分離的單一額外執行例項。 專用的執行實例可以由第三方遠程托管。 實作時，電子郵件執行、追蹤、鏡像頁面和退信訊息的處理方式與中央應用程式功能無關。

* **電源群集**

   此選項支援2到N個群集執行實例，與主Adobe Campaign應用程式實例相對於給定應用程式分離。 群集可以遠程托管、在分佈式部署中由第三方托管。 除了流程隔離的好處之外，Adobe Campaign電源群集選項還允許使用商品硬體實現冗餘和擴展策略，以簡化SLA或效能的演變。

![](assets/architectural_options_diagram.png)

## 合格申請 {#eligible-applications}

Power Booster和Power Cluster選項可用於以下應用程式：

* Campaign
* 傳遞
* 訊息中心

## 架構建議矩陣 {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>標準架構</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>電源群集</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件行銷活動和對外互動<br /> </td> 
   <td> 每月最多可達3,000萬封電子郵件<br /> </td> 
   <td> 每月3000萬至1億封電子郵件<br /> </td> 
   <td> 每月超過1億封電子郵件<br /> </td> 
  </tr> 
  <tr> 
   <td> 異動訊息<br /> </td> 
   <td> 每執行伺服器每小時50,000<br /> </td> 
   <td> 每執行伺服器每小時50,000<br /> </td> 
   <td> 每執行伺服器每小時50,000<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主資料庫的資料庫<br /> </td> 
   <td> 24/7，除了執行實例的維護窗口和下載時間之外<br /> </td> 
   <td> 24/7/365服務可能<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 資料集市可從公共網際網路訪問<br /> </td> 
   <td> 資料集市與面向網際網路的正面元件隔離<br /> </td> 
   <td> 資料集市與面向網際網路的正面元件隔離<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署模板<br /> </td> 
   <td> 所有內容都放在一個網站上（可位於內部部署或雲端中）<br /> </td> 
   <td> 可在雲端執行內部部署行銷<br /> </td> 
   <td> 在雲端執行內部部署行銷；在不同地理上執行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建議 {#recommendations}

* 執行實例必須專用於服務。 無法為尚未訂閱的服務安裝包。 例如，如果您訂閱 **Power Booster** 選項 **訊息中心** 服務，您只能安裝 **[!UICONTROL Execution of transactional messages]** 包。 請檢查您的授權合約。
* 由於專用例項（或叢集）是Adobe Campaign例項，因此建議與主要例項的建議相同。 有關詳細資訊，請參閱 [此文檔](../../production/using/foreword.md).
* 若要從資料庫/硬體元件的觀點正確配置執行個體，請聯絡Adobe Campaign Professional Services。
