---
product: campaign
title: 轉移至中間來源
description: 進一步了解轉移至中間來源工作流程
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 7%

---


# 轉移至中間來源{#transfer-to-mid-sourcing}

![](../../assets/common.svg)

以下詳細說明的工作流程會與 **轉移至中間來源** 模組。 有關此模組的詳細資訊，請參閱 [Campaign Classicv7安裝指南](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中間來源（交貨計數器）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>此工作流程會收集中間來源伺服器上傳送的計數資訊。 計數資訊包括一般傳送指標，例如傳送的傳送數量等。</p> <p>不包含開啟等追蹤資訊。</p> <p>預設會每十分鐘觸發一次。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">中間來源（傳送記錄檔）</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 此工作流程會收集中間來源伺服器上的傳送記錄。 預設會每小時觸發一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

