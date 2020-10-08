---
title: Adobe Campaign Classic中的收件匣轉換技術工作流程
description: 本節說明隨Adobe Campaign Classic中「收件匣」轉換套件安裝的技術工作流程。
page-status-flag: never-activated
uuid: f60a09f0-47a0-4fc0-b0ac-47178af6ad55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: da0779dc-b734-483b-81e9-ff4706a2b6de
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 2%

---


# 收件箱呈現(IR){#inbox-rendering}

下面詳細介紹的工作流默 **認情況下會與收件箱渲染(IR)** 模組一起安裝。 For more on Inbox rendering, refer to this [section](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>更新種子網路以生成收件箱</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span> <br /> </td> 
   <td> 此工作流程會更新用於「收件匣」轉譯的電子郵件地址，而且只有在HTTPS連接埠已開啟供 <strong>deliverability.neolane.net時，才能運作</strong>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

