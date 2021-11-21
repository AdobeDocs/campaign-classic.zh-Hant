---
product: campaign
title: 解壓縮或解密檔案
description: 了解如何在處理前先解壓縮或解密Campaign Classic中的檔案。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 11%

---

# 解壓縮或解密檔案 {#unzipping-or-decrypting-a-file-before-processing}

![](../../assets/common.svg)

Adobe Campaign可讓您匯入壓縮或加密的檔案。 以便在 [資料載入（檔案）](../../workflow/using/data-loading--file-.md) 活動中，您可以定義要解壓縮或解密檔案的預先處理。

若要這麼做：

1. 使用 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) 來產生公開/私密金鑰組。

   >[!NOTE]
   >
   >所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
   >
   >請注意，您的執行個體必須托管於AWS，並使用最新的 [Gold Standard](../../rn/using/gs-overview.md) 建置或 [最新GA版本編號(21.1.3)](../../rn/using/latest-release.md). 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)詳述的步驟操作。

1. 如果您的Adobe Campaign安裝是由Adobe托管，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 以在伺服器上安裝必要的實用程式。
1. 如果您安裝的Adobe Campaign為內部部署，請安裝您要使用的公用程式(例如：GPG、GZIP)以及應用程式伺服器上的必要金鑰（加密金鑰）。

然後，您可以將所需的預處理命令用於您的工作流程：

1. 新增及設定 **[!UICONTROL File transfer]** 活動。
1. 新增 **[!UICONTROL Data loading (file)]** 活動及定義檔案格式。
1. 核取 **[!UICONTROL Pre-process the file]** 選項。
1. 指定要套用的預處理命令。
1. 新增其他活動以管理來自檔案的資料。
1. 儲存並執行您的工作流程。

下方的使用案例提供範例。

**相關主題：**

* [資料載入（檔案）活動](../../workflow/using/data-loading--file-.md).
* [壓縮或加密檔案](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## 使用案例：匯入使用「控制面板」產生的金鑰加密的資料 {#use-case-gpg-decrypt}

在此使用案例中，我們將建立工作流程，以使用「控制面板」中產生的金鑰，匯入已在外部系統加密的資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用案例的步驟如下：

1. 使用「控制面板」產生金鑰組（公開/私人）。 如需詳細步驟，請參閱 [控制面板檔案](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * 公開金鑰將與外部系統共用，外部系統將使用該公開金鑰加密資料，以傳送至Campaign。
   * Campaign Classic將使用私鑰解密傳入的加密資料。

   ![](assets/gpg_generate.png)

1. 在外部系統中，使用從控制面板下載的公開金鑰來加密要匯入至Campaign Classic的資料。

1. 在Campaign Classic中，建立工作流程以匯入加密資料，並使用透過「控制面板」安裝的私密金鑰解密。 為此，我們將建立以下工作流程：

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 活動：將檔案從外部來源傳輸至Campaign Classic。 在此範例中，我們要從SFTP伺服器傳輸檔案。
   * **[!UICONTROL Data loading (file)]** 活動：將檔案中的資料載入到資料庫中，並使用「控制面板」中產生的私密金鑰解密。

1. 開啟 **[!UICONTROL File transfer]** 活動接著指定要從其匯入加密的.gpg檔案的外部帳戶。

   ![](assets/gpg_key_transfer.png)

   有關如何配置活動的全域概念，請參閱 [本節](../../workflow/using/file-transfer.md).

1. 開啟 **[!UICONTROL Data loading (file)]** 活動，然後根據您的需求進行設定。 有關如何配置活動的全域概念，請參閱 [本節](../../workflow/using/data-loading--file-.md).

   將預處理階段新增至活動，以解密傳入的資料。 若要這麼做，請選取 **[!UICONTROL Pre-process the file]** 選項，然後複製此解密命令並貼入 **[!UICONTROL Command]** 欄位：

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >在此示例中，我們使用「控制面板」預設使用的密碼短語，即「密碼短語」。
   >
   >如果您過去透過客戶服務請求在執行個體上安裝了GPG金鑰，則密碼可能已變更，並且依預設會有所不同。

1. 按一下 **[!UICONTROL OK]** 確認活動設定。

1. 您現在可以執行工作流程。 執行後，您可以在工作流程記錄中檢查是否已執行解密，且來自檔案的資料已匯入。

   ![](assets/gpg_run.png)

## 教學課程影片 {#video}

此影片說明如何使用GPG金鑰解密資料。

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

提供其他Campaign Classic作法影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
