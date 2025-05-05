---
product: campaign
title: 解壓縮或解密檔案
description: 瞭解在處理前如何在Campaign中解壓縮或解密檔案
feature: Workflows, Encryption
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 9%

---


# 解壓縮或解密檔案 {#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign可讓您匯入壓縮或加密的檔案。 在[資料載入（檔案）](../../workflow/using/data-loading-file.md)活動中讀取檔案之前，您可以定義解壓縮或解密檔案的預先處理。

>[!IMPORTANT]
>
>無法解壓縮大於4Gb的壓縮檔。

若要這麼做：

1. 使用[控制檯](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=zh-Hant#decrypting-data)產生公開/私密金鑰組，以允許檔案解密。

   >[!NOTE]
   >
   >所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
   >
   >請注意，您的執行個體必須託管在AWS上，並以[最新GA版本編號](../../rn/using/rn-overview.md)升級。 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)詳述的步驟操作。

1. 如果您安裝的Adobe Campaign是內部部署，請在應用程式伺服器上安裝您要使用的公用程式（例如：GPG、GZIP）以及必要的金鑰（加密金鑰）。

   如果您的Adobe Campaign安裝是由Adobe託管，請連絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，以便在伺服器上安裝必要的公用程式。

接著，您便可以在工作流程中使用所需的前置處理命令：

1. 在您的工作流程中新增及設定&#x200B;**[!UICONTROL File transfer]**&#x200B;活動。
1. 新增&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動並定義檔案格式。
1. 核取 **[!UICONTROL Pre-process the file]** 選項。
1. 選取您要套用的前置處理指令。
1. 新增其他活動以管理來自檔案的資料。
1. 儲存並執行您的工作流程。

以下的使用案例中提供範例。

**相關主題：**

* [資料載入（檔案）活動](../../workflow/using/data-loading-file.md)。
* [壓縮或加密檔案](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

## 使用案例：匯入使用控制面板產生的金鑰加密的資料 {#use-case-gpg-decrypt}

在此使用案例中，我們將建置工作流程，以使用在「控制面板」中產生的金鑰，匯入已在外部系統中加密的資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用案例的步驟如下：

1. 使用「控制面板」產生金鑰組（公用/私用）。 詳細步驟可在[控制面板檔案](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=zh-Hant#decrypting-data)中取得。

   * 公開金鑰將與外部系統共用，外部系統將使用公開金鑰來加密要傳送至Campaign的資料。
   * Campaign Classic會使用私密金鑰來解密傳入的加密資料。

   ![](assets/gpg_generate.png)

1. 在外部系統中，使用從「控制面板」下載的公開金鑰，將資料加密並匯入Campaign Classic。

1. 在Campaign Classic中，建立工作流程以匯入加密資料，並使用已透過「控制面板」安裝的私密金鑰加以解密。 為此，我們將建立工作流程，如下所示：

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]**&#x200B;活動：將檔案從外部來源傳輸至Campaign Classic。 在此範例中，我們要從SFTP伺服器傳輸檔案。
   * **[!UICONTROL Data loading (file)]**&#x200B;活動：將檔案中的資料載入資料庫，並使用在「控制面板」中產生的私密金鑰加以解密。

1. 開啟&#x200B;**[!UICONTROL File transfer]**&#x200B;活動，然後指定您要匯入加密.gpg檔案的外部帳戶。

   ![](assets/gpg_key_transfer.png)

   有關如何設定活動的全域概念可在[本節](../../workflow/using/file-transfer.md)中取得。

1. 開啟&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動，然後根據您的需求進行設定。 有關如何設定活動的全域概念可在[本節](../../workflow/using/data-loading-file.md)中取得。

   為活動新增前置處理階段，以便解密傳入的資料。 若要這麼做，請選取&#x200B;**[!UICONTROL Pre-process the file]**&#x200B;選項，然後從&#x200B;**[!UICONTROL Command]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Decrypt]**：

   ![](assets/gpg_load.png)

   >[!NOTE]
   >
   >如果可用命令需要變更，您可以聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以調整preProcessCommand設定。
   >
   >如果您使用混合式部署，可以直接從伺服器組態檔(serverConf.xml)設定這些指令。 [瞭解如何在伺服器設定檔中設定前置處理命令](../../installation/using/the-server-configuration-file.md#preprocesscommand)

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以確認活動設定。

1. 您現在可以執行工作流程。 執行之後，您可以在工作流程記錄檔中籤入已執行解密，且檔案中的資料已匯入。

   ![](assets/gpg_run.png)

## 教學課程影片 {#video}

本影片說明如何使用GPG金鑰來解密資料。

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)提供其他Campaign Classic操作說明影片。
