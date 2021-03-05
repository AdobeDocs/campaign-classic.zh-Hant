---
solution: Campaign Classic
product: campaign
title: 關於Campaign中的傳遞能力
description: 瞭解傳遞能力最佳實務
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 關於傳遞能力{#about-deliverability}

**傳遞** 能力包括測量促銷活動在到達收件者收件匣時是否成功，而不會反彈或標示為垃圾訊息。

Adobe Campaign提供特定數量的工具，以追蹤平台的可傳遞效能。 本節也說明在管理和最佳化傳遞能力時，您應牢記的主要原則。

## 設定 {#configuration}

此功能可透過Adobe Campaign的專屬套件取得。 若要使用，必須安裝此套件。 完成後，重新啟動伺服器，以便將包納入考慮範圍。
* 對於代管和混合式客戶端，**可傳遞性監控**&#x200B;是由Adobe技術支援和顧問在實例上配置的。 如需詳細資訊，請洽詢您的Adobe帳戶主管。

* 對於內部部署安裝，您必須通過&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;菜單安裝&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;軟體包。 如需詳細資訊，請參閱[安裝促銷活動內建套件](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign,**傳遞性監控**&#x200B;由&#x200B;**[!UICONTROL Refresh for deliverability]**&#x200B;工作流管理。 它預設會安裝在所有例項上，讓您初始化彈回郵件資格規則清單、網域清單和MX清單。 安裝&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;套件後，此工作流程會在每晚執行，以定期更新規則清單，並讓您主動管理平台傳遞能力。

## 背景{#background}

電子郵件傳遞能力對行銷人員而言是一項重大挑戰——不論他們要傳送幾千則訊息或數十億則。 五分之一的留言不會進入收件匣或其預定收件人。

一旦被歸為IT部門的「技術問題」，電子郵件傳遞能力就會繼續在行銷議程上佔據上風。 這是因為精明的行銷人員認識到，雖然其許多要素在本質上是技術性的，但交付性最終是一個具有重大收入影響的業務問題。

考慮電子郵件行銷漏斗。 可傳遞性決定收到的訊息數量，進而影響漏斗的每個後續階段。 收到的電子郵件較少，開啟次數更少，點按次數更少，轉換率也更少。 **對於擁有龐大資料庫的公司而言，平均傳遞能力與絕佳傳遞能力之間的差異，實際上意味著數以十萬計至數百萬美元的營收。**

![](assets/deliverability_overview_1.png)

行銷人員為了達成平均(80%)的可交付性，將大量轉化——以及美元——拋在了案頭上。

電子郵件的傳遞能力究竟是什麼？ 行銷人員如何提高傳遞率，以擴大漏鬥嘴，並從電子郵件宣傳中榨取更多成果？

電子郵件傳遞能力是指一組特性，這些特性決定了郵件通過個人電子郵件地址在短時間內到達其目的地的能力，並且在內容和格式方面具有預期的質量。 這些特徵可分為四大類：資料品質、訊息和內容、傳送基礎架構和聲譽。 它們共同構成了成功的電子郵件傳遞能力計畫的基礎。 本概述概述概述電子郵件傳送成功的四個基本要素，並提供觸及收件匣並從電子郵件行銷方案中提高營收的最佳實務。

<!--![](assets/deliverability_overview_2.png)-->
