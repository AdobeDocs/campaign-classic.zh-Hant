---
title: 轉移至中部採購
seo-title: 轉移至中部採購
description: 轉移至中部採購
seo-description: null
page-status-flag: never-activated
uuid: 6b5be5a0-d1ea-428b-a755-74dd34b1d53d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 57b873e9-e934-410b-b966-040cebd94e3e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 轉移至中部採購{#transfer-to-mid-sourcing}

依預設，下列詳細的工作流程 **會隨「轉移至中端來源** 」模組安裝。 For more on this module, refer to this [section](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中部採購（傳送計數器）</span><br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span><br /> </td> 
   <td> <p>此工作流程會收集中間採購伺服器上傳送的計數資訊。 計數資訊包括一般傳送指標，例如傳送的傳送數量等。</p> <p>不包含開啟等追蹤資訊。</p> <p>預設每10分鐘觸發一次。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中端採購（傳送記錄檔）</span><br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span><br /> </td> 
   <td> 此工作流程會收集中端採購伺服器上的傳送記錄。 預設會每小時觸發一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

