---
product: campaign
title: 隱私權資料保護規範工作流程
description: 深入了解隱私權資料保護規範工作流程
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 10%

---


# 隱私權資料保護法規{#general-data-protection-regulation-gdpr}

依預設，下列詳細的工作流程會與&#x200B;**隱私權資料保護規範**&#x200B;模組一起安裝。 有關此模組的詳細資訊，請參閱此[文章](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

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
   <td> 此工作流程會產生儲存在Adobe Campaign中的收件者資料，並讓其可在隱私權請求的畫面中下載。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刪除隱私權要求資料</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 此工作流程會刪除儲存在Adobe Campaign中的收件者資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">隱私權要求清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 此工作流將清除90天以前的訪問請求檔案。<br /> </td> 
  </tr> 
 </tbody> 
</table>

