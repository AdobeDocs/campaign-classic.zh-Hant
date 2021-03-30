---
solution: Campaign Classic
product: campaign
title: 解壓縮或解密檔案
description: 瞭解如何在處理前先解壓縮或解密Campaign Classic中的檔案。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 2%

---


# 解壓縮或解密檔案{#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign可讓您匯入壓縮或加密的檔案。 在[資料載入（檔案）](../../workflow/using/data-loading--file-.md)活動中讀取之前，您可以先定義預先處理來解壓縮或解密檔案。

若要這麼做：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)來產生公用／私用金鑰對。

   >[!NOTE]
   >
   >所有管理員使用者都可存取控制面板。 授予使用者管理員存取權的步驟詳見[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)。
   >
   >請注意，您的實例必須裝載在AWS上，並使用最新的[Gold Standard](../../rn/using/gs-overview.md)組建版本或[最新的GA組建版本(21.1)](../../rn/using/latest-release.md)進行升級。 瞭解如何在[本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本。 要檢查您的實例是否托管在AWS上，請遵循本頁[中詳細介紹的步驟。](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)

1. 如果您的Adobe Campaign安裝是由Adobe代管，請與Adobe客戶服務部門聯繫，以在伺服器上安裝必要的實用程式。[](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
1. 如果您的Adobe Campaign安裝是內部部署，請安裝您要使用的公用程式(例如：GPG、GZIP)以及應用程式伺服器上的必要金鑰（加密金鑰）。

然後，您就可以在工作流程中使用所需的預處理命令：

1. 在工作流程中新增及設定&#x200B;**[!UICONTROL File transfer]**&#x200B;活動。
1. 新增&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動並定義檔案格式。
1. 核取 **[!UICONTROL Pre-process the file]** 選項。
1. 指定要套用的預處理命令。
1. 新增其他活動以管理來自檔案的資料。
1. 儲存並執行您的工作流程。

在下面的使用案例中提供了示例。

**相關主題：**

* [資料載入（檔案）活動](../../workflow/using/data-loading--file-.md)。
* [壓縮或加密檔案](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

## 使用案例：使用控制面板{#use-case-gpg-decrypt}產生的金鑰匯入加密的資料

在此使用案例中，我們將建立工作流程，以便使用「控制面板」中產生的金鑰，匯入在外部系統中加密的資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用案例的步驟如下：

1. 使用「控制面板」產生金鑰對（公開／私用）。 有關詳細步驟，請參閱[控制面板文檔](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)。

   * 公開金鑰將會與外部系統共用，外部系統會使用它來加密要傳送至Campaign的資料。
   * 私密金鑰將由Campaign Classic用來解密傳入的加密資料。

   ![](assets/gpg_generate.png)

1. 在外部系統中，使用從控制面板下載的公開金鑰來加密要導入Campaign Classic的資料。

1. 在Campaign Classic中，建立工作流程以匯入加密的資料，並使用透過控制面板安裝的私密金鑰加以解密。 為此，我們將建立以下工作流程：

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 活動：將檔案從外部源傳輸到Campaign Classic。在此範例中，我們要從SFTP伺服器傳輸檔案。
   * **[!UICONTROL Data loading (file)]** 活動：將檔案中的資料載入到資料庫中，然後使用「控制面板」中生成的專用密鑰對其進行解密。

1. 開啟&#x200B;**[!UICONTROL File transfer]**&#x200B;活動，然後指定您要從中匯入加密。gpg檔案的外部帳戶。

   ![](assets/gpg_key_transfer.png)

   有關如何配置活動的全局概念，請參閱[本節](../../workflow/using/file-transfer.md)。

1. 開啟&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動，然後根據您的需求進行設定。 有關如何配置活動的全局概念可在[本節](../../workflow/using/data-loading--file-.md)中獲得。

   將預處理階段添加到活動中，以便解密傳入資料。 要執行此操作，請選擇&#x200B;**[!UICONTROL Pre-process the file]**&#x200B;選項，然後在&#x200B;**[!UICONTROL Command]**&#x200B;欄位中複製並貼上此解密命令：

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >在此示例中，我們使用「控制面板」預設使用的密碼短語，即「密碼短語」。
   >
   >如果您過去透過客戶服務要求在實例上安裝了GPG金鑰，密碼短語可能已變更，而且依預設會與密碼短語不同。

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;確認活動配置。

1. 您現在可以執行工作流程。 執行完該操作後，您可以簽入工作流日誌，確認已執行解密，且已導入檔案中的資料。

   ![](assets/gpg_run.png)

## 教學課程影片{#video}

本視訊說明如何使用GPG金鑰解密資料。

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

其他Campaign Classichow-to影片可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
