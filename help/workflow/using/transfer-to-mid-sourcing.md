---
solution: Campaign Classic
product: campaign
title: 轉移至中間來源
description: 進一步瞭解轉移至中部採購工作流程
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# 轉移至中間來源{#transfer-to-mid-sourcing}

以下詳細說明的工作流預設隨&#x200B;**Transfer to Mid-Sourcing**&#x200B;模組一起安裝。 有關此模組的詳細資訊，請參閱此[部分](../../installation/using/mid-sourcing-deployment.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中部採購（交貨計數器）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>此工作流程會收集中間採購伺服器上傳送的計數資訊。 計數資訊包括一般傳送指標，例如傳送的傳送數量等。</p> <p>不包含開啟等追蹤資訊。</p> <p>預設每10分鐘觸發一次。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中端採購（交貨記錄）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 此工作流程會收集中端採購伺服器上的傳送記錄。 預設會每小時觸發一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

