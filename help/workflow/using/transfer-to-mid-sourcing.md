---
product: campaign
title: 轉移至中間來源
description: 進一步了解轉移至中間來源工作流程
feature: Workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 1%

---


# 轉移至中間來源{#transfer-to-mid-sourcing}



以下詳述的工作流程會隨 **轉移至中間來源** 模組（預設）。 有關本模組的詳細資訊，請參閱 [Campaign Classic v7安裝指南](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中間來源（傳遞計數器）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>此工作流程會收集中間來源伺服器上傳遞的計數資訊。 計數資訊包括一般傳遞指標，例如已傳送的傳遞數量等。</p> <p>未包含開啟之類的追蹤資訊。</p> <p>預設會每十分鐘觸發一次。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中間來源（傳遞記錄）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 此工作流程會收集中間來源伺服器上的傳遞記錄。 預設會每小時觸發一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

