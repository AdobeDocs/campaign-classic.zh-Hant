---
product: campaign
title: 將Adobe Experience Platform區段擷取至Campaign
description: 瞭解如何將Adobe Experience Platform受眾內嵌至Campaign Classic
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
TQID: https://experienceleague.adobe.com/gZ3arUya5UYcZckqtlDObZTA7laUmVttTDHxgOb97vE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 0%

---

# 將Adobe Experience Platform區段擷取至Campaign {#destinations}



若要將Adobe Experience Platform對象擷取至Campaign並用於您的工作流程，您首先需要將Adobe Campaign as a Adobe Experience Platform **目的地**&#x200B;連線，並使用要匯出的區段進行設定。

設定目的地後，系統會將資料匯出至您的儲存位置，而且您將需要在Campaign Classic中建置專用的工作流程來擷取資料。

## 將Adobe Campaign連線為目的地

在Adobe Experience Platform中，選取匯出區段的儲存位置，以設定與Adobe Campaign的連線。 此步驟也可讓您選取要匯出的區段，並指定要包含的其他XDM欄位。

如需詳細資訊，請參閱[Destinations檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)。

設定目的地後，Adobe Experience Platform會在您提供的儲存位置中建立以Tab分隔的.txt或.csv檔案。 此作業會排程並每24小時執行一次。

您現在可以設定Campaign Classic工作流程，將區段擷取至Campaign。

## 在Campaign Classic中建立匯入工作流程

將Campaign Classic設定為目的地後，您需要建立專用的工作流程，以匯入Adobe Experience Platform已匯出的檔案。

若要這麼做，您必須新增及設定&#x200B;**[!UICONTROL File transfer]**&#x200B;活動。 有關如何設定此活動的詳細資訊，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html){target="_blank"}。

![](assets/rtcdp-file-transfer.png)

接著，您就可以根據需求建立工作流程（使用區段資料更新資料庫、傳送跨管道傳遞至區段等）

例如，以下工作流程會每天從您的儲存位置下載檔案，然後使用區段資料更新Campaign資料庫。

![](assets/rtcdp-workflow.png)
