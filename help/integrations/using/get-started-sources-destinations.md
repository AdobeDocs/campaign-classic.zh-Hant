---
product: campaign
title: 開始使用來源和目標
description: 進一步了解Adobe Experience Platform來源和目的地。
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 6%

---

# 開始使用來源和目標 {#rtcdp}

![](../../assets/common.svg)

## 關於來源和目的地

透過Adobe Experience Platform，您可以在Campaign Classic和Adobe即時客戶資料平台(RTCDP)之間共用資料。 這可讓您在促銷活動工作流程中鎖定Adobe Experience Platform對象，然後傳回至Adobe即時客戶資料平台與這些對象相關的資料，例如傳送、開啟和點按。

* 透過&#x200B;**Destinations**，將對象從Adobe Experience Platform擷取至Campaign Classic。 這可讓您為行銷活動啟用已知和未知的資料。
* 透過&#x200B;**Sources**，將Campaign Classic資料（例如傳送、開啟、點按）匯出至Adobe Experience Platform。 這可讓您將從不同來源收集的資料集中到單一位置，並利用從中獲得的分析功能完成更多工作。

>[!IMPORTANT]
>
>執行此整合時，請記得您的Adobe Campaign合約所規定的SFTP儲存限制、資料庫儲存限制和作用中設定檔限制。

如需Adobe即時客戶資料平台、目的地和來源的更詳細概覽，請參閱下列頁面：

* [Adobe即時客戶資料平台](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
* [目的地檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html)
* [來源檔案](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

## 連線Campaign Classic與Adobe Experience Platform

若要在Adobe Experience Platform和Campaign Classic之間共用資料，您首先需要以&#x200B;**Destination**&#x200B;連接Adobe Campaign，並將您的AWS S3或Azure Blob儲存位置以&#x200B;**Source**&#x200B;在Adobe體驗平台中連接。

在設定連接器後，您可以使用工作流程來設定資料匯入或匯出至Campaign Classic。

![](assets/rtcdp-schema.png)

有關如何設定這些匯入和匯出程式的詳細資訊，請參閱以下章節：

* [將Adobe Experience Platform區段內嵌至Campaign](../../integrations/using/ingest-aep-data.md)
* [將資料從 Campaign 匯出至 Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
