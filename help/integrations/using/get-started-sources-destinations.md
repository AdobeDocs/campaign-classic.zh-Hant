---
solution: Campaign Classic
product: campaign
title: 開始使用來源和目標
description: 進一步瞭解Adobe Experience Platform來源和目的地。
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: b4da54c122e75a175f6f586a05955b3dfed00c1e
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# 開始使用Sources和Destinations {#rtcdp}

## 關於來源和目標

借助Adobe Experience Platform，您可以在Campaign Classic和Adobe即時客戶資料平台(RTCDP)之間共用資料。 這可讓您在促銷活動工作流程中鎖定Adobe Experience Platform受眾，然後傳回至Adobe即時客戶資料平台資料，這些資料與這些受眾相關，例如傳送、開啟和點按。

* 透過&#x200B;**目標**，將來自Adobe Experience Platform的觀眾收錄至Campaign Classic。 這可讓您啟用行銷活動的已知和未知資料。
* 使用&#x200B;**Sources**，將Campaign Classic資料（例如傳送、開啟、點按）匯出至Adobe Experience Platform。 這可讓您將從不同來源收集的資料集中到單一位置，並運用從中獲得的見解完成更多工作。

>[!IMPORTANT]
>
>執行此項整合時，請記住SFTP儲存限制、資料庫儲存限制和作用中的設定檔限制(依您的Adobe Campaign合約)。

有關Adobe即時客戶資料平台、目標和源的更詳細概覽，請參閱以下頁：

* [Adobe即時客戶資料平台](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
* [目標檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html)
* [來源檔案](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

## 連接Campaign Classic與Adobe Experience Platform

為了能夠在Adobe Experience Platform和Campaign Classic之間共用資料，您首先需要將Adobe Campaign連接為&#x200B;**目標**，並將AWS S3或Azure blob儲存位置連接為Adobe體驗平台中的&#x200B;**源**。

在配置連接器後，您可以使用工作流設定資料導入或導出到Campaign Classic。

![](assets/rtcdp-schema.png)

有關如何設定這些導入和導出流程的詳細資訊，請參閱以下各節：

* [將Adobe Experience Platform區段內嵌至Campaign](../../integrations/using/ingest-aep-data.md)
* [將資料從Campaign匯出至Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
