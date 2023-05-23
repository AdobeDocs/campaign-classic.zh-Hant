---
product: campaign
title: 壓縮或加密檔案
description: 在處理之前，瞭解如何在市場活動中壓縮或加密檔案
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 8%

---

# 壓縮或加密檔案 {#zipping-or-encrypting-a-file}



Adobe Campaign允許導出壓縮或加密檔案。 通過定義導出時 **[!UICONTROL Data extraction (file)]** 活動，您可以定義後處理來壓縮或加密檔案。

要做到這一點：

1. 使用 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)。

   >[!NOTE]
   >
   >控制面板僅限於管理員用戶，並且僅適用於某些市場活動版本。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)

1. 如果您的Adobe Campaign安裝由Adobe托管，請聯繫 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 在伺服器上安裝必要的實用程式。
1. 如果您的Adobe Campaign安裝是本地安裝，請安裝您要使用的實用程式(例如：GPG 、 GZIP)以及應用程式伺服器上必需的密鑰（加密密鑰）。

然後，可在 **[!UICONTROL Script]** 頁籤 **[!UICONTROL JavaScript code]** 的子菜單。 在下面的使用案例中給出了一個示例。

**相關主題：**

* [在處理前先解壓縮或解密檔案](../../platform/using/unzip-decrypt.md)
* [資料提取（檔案）活動](../../workflow/using/extraction--file-.md)。

## 用例：使用控制面板上安裝的密鑰加密和導出資料 {#use-case-gpg-encrypt}

在此使用情形中，我們將構建一個工作流，以便使用控制面板上安裝的密鑰加密和導出資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用情形的步驟如下：

1. 使用GPG實用程式生成GPG密鑰對（公共/私有），然後將公鑰安裝到控制面板上。 有關詳細步驟，請參閱 [控制面板文檔](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)。

1. 在Campaign Classic中，構建工作流以導出資料並使用通過控制面板安裝的私鑰對其進行加密。 為此，我們將按照以下方式構建工作流：

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 活動：在此示例中，我們要執行查詢以針對要從要導出的資料庫中的資料。
   * **[!UICONTROL Data extraction (file)]** 活動：將資料提取到檔案中。
   * **[!UICONTROL JavaScript code]** 活動：加密要提取的資料。
   * **[!UICONTROL File transfer]** 活動：將資料發送到外部源（在本例中為SFTP伺服器）。

1. 配置 **[!UICONTROL Query]** 活動，以從資料庫中確定所需資料的目標。 如需詳細資訊，請參閱[本章節](../../workflow/using/query.md)。

1. 開啟 **[!UICONTROL Data extraction (file)]** 活動，然後根據您的需要配置。 有關如何配置活動的全局概念，請參見 [此部分](../../workflow/using/extraction--file-.md)。

   ![](assets/gpg-data-extraction.png)

1. 開啟 **[!UICONTROL JavaScript code]** 活動，然後複製並貼上下面的命令以加密要提取的資料。

   >[!IMPORTANT]
   >
   >確保替換 **指紋** 命令中的值，其中公共密鑰的指紋安裝在控制面板上。

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

1. 開啟 **[!UICONTROL File transfer]** 活動，然後指定要向其發送檔案的SFTP伺服器。 有關如何配置活動的全局概念，請參見 [此部分](../../workflow/using/file-transfer.md)。

   ![](assets/gpg-file-transfer.png)

1. 您現在可以運行工作流。 一旦執行，查詢所生成的資料目標將導出到SFTP伺服器中，並生成加密的.gpg檔案。

## 教程視頻 {#video}

此視頻還顯示了如何使用GPG密鑰加密資料

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

可提供其他Campaign Classic操作視頻 [這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)。
