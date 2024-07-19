---
product: campaign
title: Power Booster 與 Power Cluster
description: Power Booster 與 Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 6%

---

# Power Booster 與 Power Cluster{#power-booster-and-power-cluster}



## 概覽 {#overview}

Adobe Campaign提供兩組預先封裝的架構選項，供您設定部署的維度：

* **Power Booster**

  此選項可支援與主要Adobe Campaign應用程式執行個體分離的單一額外執行執行個體。 專屬執行例項可由遠端或協力廠商託管。 實施時，電子郵件執行、追蹤、映象頁面和退回訊息的處理與中央應用程式功能無關。

* **電源叢集**

  此選項可支援與指定應用程式相關之主要Adobe Campaign應用程式執行個體分離的2到N個叢集執行個體。 叢集可以遠端託管、在分散式部署中由協力廠商託管。 除了流程隔離的好處外，Adobe Campaign Power Cluster選項還可使用商品硬體來啟用備援和向外擴充策略，以簡化SLA或效能的演化。

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
   <td> 每月最多約3,000萬封電子郵件<br /> </td> 
   <td> 每月3000到1億封電子郵件<br /> </td> 
   <td> 每月超過1億封電子郵件<br /> </td> 
  </tr> 
  <tr> 
   <td> 異動訊息<br /> </td> 
   <td> 每執行伺服器<br />每小時50,000次 </td> 
   <td> 每執行伺服器<br />每小時50,000次 </td> 
   <td> 每執行伺服器<br />每小時50,000次 </td> 
  </tr> 
  <tr> 
   <td> 可用性<br /> </td> 
   <td> 主要資料庫<br />的 </td> 
   <td> 除了執行執行個體的維護期間和停機時間，24/7天<br /> </td> 
   <td> 24/7/365可能的服務<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全性<br /> </td> 
   <td> 可以從公用網際網路存取資料市場<br /> </td> 
   <td> 資料超市與正面、面向網際網路的元件隔離<br /> </td> 
   <td> 資料超市與正面、面向網際網路的元件隔離<br /> </td> 
  </tr> 
  <tr> 
   <td> 部署範本<br /> </td> 
   <td> 全部位於單一網站（可以是內部部署或雲端）<br /> </td> 
   <td> 可在雲端中執行的內部部署行銷<br /> </td> 
   <td> 在雲端中執行的內部部署行銷；可在不同的地理位置執行<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 建議 {#recommendations}

* 執行例項必須專用於服務。 您無法為尚未訂閱的服務安裝套件。 例如，如果您訂閱&#x200B;**訊息中心**&#x200B;服務的&#x200B;**Power Booster**&#x200B;選項，則只能在專用執行例項上安裝&#x200B;**[!UICONTROL Execution of transactional messages]**&#x200B;套件。 請檢查您的授權合約。
* 由於專用執行個體（或叢集）是Adobe Campaign執行個體，因此建議與主要執行個體相同。 如需詳細資訊，請參閱[此檔案](../../production/using/foreword.md)。
* 若要從資料庫/硬體元件檢視正確設定執行個體，請聯絡Adobe Campaign Professional Services。
