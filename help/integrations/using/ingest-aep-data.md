---
product: campaign
title: 將Adobe Experience Platform區段擷取至Campaign
description: 瞭解如何將Adobe Experience Platform受眾擷取至Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 將Adobe Experience Platform區段擷取至Campaign {#destinations}



若要將Adobe Experience Platform受眾擷取至Campaign並在您的工作流程中使用，您首先需要連線Adobe Campaign as a Adobe Experience Platform **目的地** 並設定為要匯出的區段。

設定目的地後，會將資料匯出至您的儲存位置，而且您將需要以Campaign Classic建置專用的工作流程來擷取資料。

## 將Adobe Campaign連線為目的地

在Adobe Experience Platform中，選取匯出區段的儲存位置，以設定與Adobe Campaign的連線。 此步驟也可讓您選取要匯出的區段，並指定要包含的其他XDM欄位。

如需詳細資訊，請參閱 [目的地檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

設定目的地後，Adobe Experience Platform會在您提供的儲存位置中建立以Tab分隔的.txt或.csv檔案。 此作業會排程並每24小時執行一次。

您現在可以設定Campaign Classic工作流程，將區段擷取至Campaign。

## 在Campaign Classic中建立匯入工作流程

將Campaign Classic設定為目的地後，您需要建立專屬的工作流程，以匯入Adobe Experience Platform已匯出的檔案。

為此，您需要新增並設定 **[!UICONTROL File transfer]** 活動。 有關如何設定此活動的詳細資訊，請參閱 [本節](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

接著，您就可以視需要建置工作流程（使用區段資料更新資料庫、傳送跨管道傳遞至區段等）

例如，以下工作流程會每天從您的儲存位置下載檔案，然後使用區段資料更新Campaign資料庫。

![](assets/rtcdp-workflow.png)
