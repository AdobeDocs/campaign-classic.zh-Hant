---
product: campaign
title: Power Booster 與 Power Cluster
description: Power Booster 與 Power Cluster
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 7%

---

# Power Booster 與 Power Cluster{#power-booster-and-power-cluster}



## 概覽 {#overview}

Adobe Campaign提供兩組預先封裝的架構選項，用於設定部署的維度：

* **Power Booster**

   此選項支援與主要Adobe Campaign應用程式執行個體分離的單一額外執行執行個體。 專用的執行例項可由遠端主控或由第三方主控。 實施後，電子郵件執行、追蹤、映象頁面和退回訊息的處理會與中央應用程式功能無關。

* **電源叢集**

   此選項可支援與指定應用程式相關之主要Adobe Campaign應用程式執行個體分離的2到N個叢集執行個體。 叢集可由遠端託管、分散式部署及協力廠商。 除了流程隔離的好處之外，Adobe Campaign電源群集選項還能夠使用商品化硬體來啟用備援和向外擴充策略，以簡化SLA或效能的演化。

![](assets/architectural_options_diagram.png)

## 符合資格的應用程式 {#eligible-applications}

Power Booster和Power Cluster選項可供下列應用程式使用：

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
   <td> <strong>電源叢集</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件行銷活動和對外互動<br /> </td> 
   <td> 每月最多可達3,000萬封電子郵件<br /> </td> 
   <td> 每月傳送3,000萬到1億封電子郵件<br /> </td> 
   <td> 每月超過1億封電子郵件<br /> </td> 
  </tr> 
  <tr> 
   <td> 異動訊息<br /> </td> 
   <td> 每部執行伺服器每小時50,000次<br /> </td> 
   <td> 每部執行伺服器每小時50,000次<br /> </td> 
   <td> 每部執行伺服器每小時50,000次<br /> </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主要資料庫的<br /> </td> 
   <td> 除了執行例項的維護時段和停機時間，全年無休<br /> </td> 
   <td> 24/7/365全年無休的服務<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 您可以從公用網際網路存取資料市場<br /> </td> 
   <td> 資料市場與面向網際網路的正面元件隔離<br /> </td> 
   <td> 資料市場與面向網際網路的正面元件隔離<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署範本<br /> </td> 
   <td> 全部位於一個網站上（可在內部部署或在雲端中）<br /> </td> 
   <td> 可在雲端中執行的內部部署行銷<br /> </td> 
   <td> 內部部署行銷，在雲端中執行；可在不同地理位置執行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建議 {#recommendations}

* 執行例項必須專屬於服務。 您無法為尚未訂閱的服務安裝套件。 例如，如果您訂閱 **Power Booster** 的選項 **訊息中心** 服務，您只能安裝 **[!UICONTROL Execution of transactional messages]** 專屬執行例項上的套件。 請檢查您的授權合約。
* 由於專用執行個體（或叢集）是Adobe Campaign執行個體，因此建議與主要執行個體的建議相同。 有關詳細資訊，請參閱 [本檔案](../../production/using/foreword.md).
* 若要從資料庫/硬體元件角度正確設定執行個體，請聯絡Adobe Campaign Professional Services。
