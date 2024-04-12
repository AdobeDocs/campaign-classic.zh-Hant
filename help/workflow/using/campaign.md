---
product: campaign
title: Campaign
description: Campaign
feature: Workflows
topic-tags: technical-workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# Campaign{#campaign}



以下詳述的工作流程會隨 **Campaign** 模組（預設）。 如需此模組的詳細資訊，請參閱此 [區段](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>為了在行銷活動層級執行行銷活動程式，必須啟動這些工作流程。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">成本計算</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> 此工作流程會開始計算預算、計畫、方案、行銷活動、傳遞和任務的費用和成本行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">庫存：訂單與警示</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> 此工作流程會啟動訂單明細行的庫存計算，並管理警告警示臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">行銷活動中傳遞的工作</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> 此工作流程會觸發已核准的傳送，並開始為外部傳送對服務提供者進行後續處理。 也會傳送核准通知和提醒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">行銷活動工作</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> 此工作流程管理行銷活動的工作（啟動目標定位、檔案擷取等）。 也會建立與循環和定期行銷活動相關的工作流程。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">服務提供者上的工作</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> 在核准傳遞後，此工作流程會開始處理提供者（傳送至路由器的電子郵件並進行後續處理）。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

