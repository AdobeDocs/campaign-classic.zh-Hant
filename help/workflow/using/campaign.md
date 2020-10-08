---
title: Campaign
seo-title: Campaign
description: Campaign
seo-description: null
page-status-flag: never-activated
uuid: 9e5cf203-e5e9-4383-b628-aa6f131491e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: de892ec4-c378-4b22-875e-aa9345f82552
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 3%

---


# Campaign{#campaign}

依預設，下列詳細的工作流程會隨 **Campaign** 模組一起安裝。 For more on this module, refer to this [section](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>必須啟動這些工作流程，才能在促銷活動層級執行促銷活動程式。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">成本計算</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMagt</span> <br /> </td> 
   <td> 此工作流將開始計算預算、計畫、方案、促銷活動、交貨和任務上的費用和成本行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">股票：訂購與警報</span> <br /> </td> 
   <td> <span class="uicontrol">stockMagt</span> <br /> </td> 
   <td> 此工作流會在訂單行上啟動庫存計算並管理警告警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">促銷活動中傳送的工作</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMagt</span> <br /> </td> 
   <td> 此工作流程會觸發已核准的傳送，並開始對外部傳送的服務提供者進行後處理。 它也會傳送核准通知和提醒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">促銷活動工作</span> <br /> </td> 
   <td> <span class="uicontrol">operationMagt</span> <br /> </td> 
   <td> 此工作流程管理行銷促銷活動的工作（啟動定位、檔案擷取等）。 它也會建立與週期性和週期性促銷活動相關的工作流程。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">服務提供者的工作</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMagt</span> <br /> </td> 
   <td> 一旦交件獲得批准，此工作流將開始處理提供程式（向路由器發送電子郵件和後處理）。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

