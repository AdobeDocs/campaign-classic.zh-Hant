---
product: campaign
title: 隱私權資料保護規範工作流程
description: 進一步瞭解隱私權資料保護規則工作流程
hide: true
hidefromtoc: true
feature: Workflows, Privacy
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 2%

---


# 隱私權資料保護規範{#general-data-protection-regulation-gdpr}



依預設，以下詳細描述的工作流程會與&#x200B;**隱私權資料保護規範**&#x200B;模組一併安裝。 如需此模組的詳細資訊，請參閱此[文章](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

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
   <td> 此工作流程會產生儲存在Adobe Campaign的收件者資料，並讓該資料可在隱私權請求的畫面中下載。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刪除隱私權要求資料</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 此工作流程會刪除收件者儲存在Adobe Campaign中的資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">隱私權要求清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 此工作流程會清除90天以前的存取要求檔案。<br /> </td> 
  </tr> 
 </tbody> 
</table>

