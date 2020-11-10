---
title: 隱私權資料保護法規工作流程
description: 進一步瞭解隱私權資料保護法規工作流程
page-status-flag: never-activated
uuid: cb5f5d79-52ac-4ce4-abc7-a3a1f0a001cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 050c804e-87b7-4d68-b787-c396fec329d2
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 10%

---


# 隱私權資料保護法規{#general-data-protection-regulation-gdpr}

依預設，下列詳細的工作流程會隨 **「隱私資料保護規則** 」模組安裝。 For more on this module, refer to this [article](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">收集隱私權要求</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> 此工作流程會產生儲存在Adobe Campaign中的收件者資料，並讓該資料可在隱私權要求的畫面中下載。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刪除隱私權要求資料</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 此工作流程會刪除Adobe Campaign中儲存的收件者資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">隱私權要求清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 此工作流程會清除90天以前的存取要求檔案。<br /> </td> 
  </tr> 
 </tbody> 
</table>

