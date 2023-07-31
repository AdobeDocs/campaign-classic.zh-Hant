---
product: campaign
title: 壓縮或加密檔案
description: 瞭解處理前如何在Campaign中壓縮或加密檔案
feature: Data Management
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 8%

---

# 壓縮或加密檔案 {#zipping-or-encrypting-a-file}



Adobe Campaign可讓您匯出壓縮或加密的檔案。 透過定義匯出時 **[!UICONTROL Data extraction (file)]** 活動，您可以將後處理定義為zip或加密檔案。

若要這麼做：

1. 使用為您的執行個體安裝GPG金鑰組 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >「控制面板」僅限管理員使用者使用，且僅適用於特定Campaign版本。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)
   >

1. 如果您的Adobe Campaign安裝是由Adobe託管，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 在伺服器上安裝必要的公用程式。
1. 如果您安裝的Adobe Campaign是內部部署，請在應用程式伺服器上安裝您要使用的公用程式（例如：GPG、GZIP）以及必要的金鑰（加密金鑰）。

然後，您便可以在以下位置使用命令或程式碼： **[!UICONTROL Script]** 活動的索引標籤或 **[!UICONTROL JavaScript code]** 活動。 以下的使用案例中提供範例。

**相關主題：**

* [在處理前先解壓縮或解密檔案](../../platform/using/unzip-decrypt.md)
* [資料擷取（檔案）活動](../../workflow/using/extraction--file-.md).

## 使用案例：使用安裝於控制面板的金鑰加密及匯出資料 {#use-case-gpg-encrypt}

在此使用案例中，我們將建立工作流程，以使用安裝於控制面板的金鑰加密及匯出資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用案例的步驟如下：

1. 使用GPG公用程式產生GPG金鑰組（公用/私用），然後將公用金鑰安裝至「控制面板」。 詳細步驟請參閱 [控制面板檔案](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. 在Campaign Classic中，建立工作流程以匯出資料，並使用已透過「控制面板」安裝的私密金鑰進行加密。 為此，我們將建立工作流程，如下所示：

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 活動：在此範例中，我們要執行查詢，以定位要匯出的資料庫資料。
   * **[!UICONTROL Data extraction (file)]** 活動：將資料擷取至檔案中。
   * **[!UICONTROL JavaScript code]** 活動：加密資料以擷取。
   * **[!UICONTROL File transfer]** 活動：將資料傳送至外部來源（在此範例中為SFTP伺服器）。

1. 設定 **[!UICONTROL Query]** 活動，從資料庫中鎖定所需的資料。 如需詳細資訊，請參閱[本章節](../../workflow/using/query.md)。

1. 開啟 **[!UICONTROL Data extraction (file)]** 活動，然後根據您的需求進行設定。 有關如何設定活動的全域概念，請參閱 [本節](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. 開啟 **[!UICONTROL JavaScript code]** 活動，然後複製並貼上下列命令以加密要擷取的資料。

   >[!IMPORTANT]
   >
   >請務必取代 **指紋** 值，此值來自於「控制面板」上所安裝公開金鑰指紋的命令。

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

1. 開啟 **[!UICONTROL File transfer]** 活動，然後指定您要傳送檔案的SFTP伺服器。 有關如何設定活動的全域概念，請參閱 [本節](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. 您現在可以執行工作流程。 一旦執行後，查詢的資料目標將會匯出至SFTP伺服器加密的.gpg檔案中。

## 教學課程影片 {#video}

本影片說明如何使用GPG金鑰加密資料，也可參閱

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

提供其他Campaign Classic操作影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
