---
product: campaign
title: 開始使用來源和目標
description: 進一步瞭解Adobe Experience Platform來源和目標
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 10%

---

# 使用來源和目的地 {#rtcdp}



## 關於來源和目的地

透過Adobe Experience Platform，您可以在Campaign Classic和Adobe Real-time Customer Data Platform (RTCDP)之間共用資料。 這可讓您在行銷活動工作流程中鎖定Adobe Experience Platform對象，然後傳回Adobe Real-time Customer Data Platform中與這些對象相關的資料，例如傳送、開啟和點按。

* 使用&#x200B;**Destinations**，將對象從Adobe Experience Platform擷取到Campaign Classic。 這可讓您針對行銷活動啟用已知和未知的資料。
* 透過&#x200B;**來源**，將Campaign Classic資料（例如傳送、開啟、點按）匯出至Adobe Experience Platform。 這可讓您將從不同來源收集的資料集中到單一位置，並使用從中獲得的見解做更多工作。

>[!IMPORTANT]
>
>在執行此整合時，請謹記Adobe Campaign合約中的SFTP儲存空間限制、資料庫儲存空間限制和作用中設定檔限制。

如需Adobe Real-time Customer Data Platform、「目的地」和「來源」的詳細概觀，請參閱以下頁面：

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=zh-Hant)
* [目的地文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=zh-Hant)
* [來源文件](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hant)

## 連結Campaign Classic與Adobe Experience Platform

若要能夠在Adobe Experience Platform和Campaign Classic之間共用資料，您必須先連線Adobe Campaign做為&#x200B;**目的地**，並在Adobe Experience Platform中將您的AWS S3或Azure Blob儲存位置做為&#x200B;**Source**。

聯結器設定完成後，您可以使用工作流程設定資料匯入或匯出至Campaign Classic。

![](assets/rtcdp-schema.png)

如需如何設定這些匯入和匯出流程的詳細資訊，請參閱以下章節：

* [將Adobe Experience Platform區段擷取至Campaign](../../integrations/using/ingest-aep-data.md)
* [將資料從 Campaign 匯出至 Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
