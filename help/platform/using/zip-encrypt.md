---
solution: Campaign Classic
product: campaign
title: 壓縮或加密檔案
description: 瞭解如何在處理前先在Campaign Classic中壓縮或加密檔案。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# 壓縮或加密檔案{#zipping-or-encrypting-a-file}

Adobe Campaign可讓您匯出壓縮或加密的檔案。 當透過&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活動定義匯出時，您可以定義後置處理，以壓縮或加密檔案。

若要這麼做：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)為實例安裝GPG密鑰對。

   >[!NOTE]
   >
   >控制面板適用於AWS托管的所有客戶（現場托管其行銷實例的客戶除外）。

1. 如果您的Adobe Campaign安裝是由Adobe代管，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，以便在伺服器上安裝必要的公用程式。
1. 如果您的Adobe Campaign安裝是內部部署，請安裝您要使用的公用程式(例如：GPG、GZIP)以及應用程式伺服器上的必要金鑰（加密金鑰）。

然後，您可以在活動的&#x200B;**[!UICONTROL Script]**&#x200B;標籤或&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動中使用命令或代碼。 在下面的使用案例中提供了示例。

**相關主題：**

* [在處理前解壓縮或解密檔案](../../platform/using/unzip-decrypt.md)
* [資料擷取（檔案）活動](../../workflow/using/extraction--file-.md)。

## 使用案例：使用控制面板{#use-case-gpg-encrypt}上安裝的密鑰加密和導出資料

在此使用案例中，我們將建立工作流程，以便使用「控制面板」上安裝的金鑰來加密和匯出資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用案例的步驟如下：

1. 使用GPG公用程式產生GPG金鑰對（公用／私用），然後將公用金鑰安裝至「控制面板」。 [控制面板文檔](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)中提供了詳細步驟。

1. 在Campaign Classic中，建立工作流程以匯出資料，並使用透過控制面板安裝的私密金鑰加密資料。 為此，我們將建立以下工作流程：

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 活動：在此示例中，我們要執行查詢來定位要導出的資料庫中的資料。
   * **[!UICONTROL Data extraction (file)]** 活動：將資料擷取至檔案。
   * **[!UICONTROL JavaScript code]** 活動：加密要提取的資料。
   * **[!UICONTROL File transfer]** 活動：將資料傳送至外部來源（在此範例中為SFTP伺服器）。

1. 配置&#x200B;**[!UICONTROL Query]**&#x200B;活動以定位資料庫中所需的資料。 如需詳細資訊，請參閱[本章節](../../workflow/using/query.md)。

1. 開啟&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活動，然後根據您的需求進行設定。 有關如何配置活動的全局概念，請參閱[本節](../../workflow/using/extraction--file-.md)。

   ![](assets/gpg-data-extraction.png)

1. 開啟&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動，然後複製並貼上下方的命令，以加密要擷取的資料。

   >[!IMPORTANT]
   >
   >請務必將命令中的&#x200B;**指紋**&#x200B;值替換為控制面板上安裝的公鑰的指紋。

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. 開啟&#x200B;**[!UICONTROL File transfer]**&#x200B;活動，然後指定您要傳送檔案的SFTP伺服器。 有關如何配置活動的全局概念可在[本節](../../workflow/using/file-transfer.md)中獲得。

   ![](assets/gpg-file-transfer.png)

1. 您現在可以執行工作流程。 執行後，查詢的資料目標將匯出至SFTP伺服器，並匯出至加密的。gpg檔案。

## 教學課程影片{#video}

此視訊說明如何使用GPG金鑰來加密資料，也可在

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

其他Campaign Classic操作視訊可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
