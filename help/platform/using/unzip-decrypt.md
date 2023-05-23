---
product: campaign
title: 解壓縮或解密檔案
description: 瞭解如何在處理之前解壓縮或解密市場活動中的檔案
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 10%

---

# 解壓縮或解密檔案 {#unzipping-or-decrypting-a-file-before-processing}



Adobe Campaign允許您導入壓縮或加密檔案。 在它們被讀入 [資料載入（檔案）](../../workflow/using/data-loading--file-.md) 活動，您可以定義一個預處理以解壓縮或解密檔案。

要做到這一點：

1. 使用 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) 生成公共/私有密鑰對。

   >[!NOTE]
   >
   >所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
   >
   >請注意，您的實例必須托管在AWS上，並使用 [最新的GA版本](../../rn/using/rn-overview.md)。 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)詳述的步驟操作。

1. 如果您的Adobe Campaign安裝由Adobe托管，請聯繫 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 在伺服器上安裝必要的實用程式。
1. 如果您的Adobe Campaign安裝是本地安裝，請安裝您要使用的實用程式(例如：GPG 、 GZIP)以及應用程式伺服器上必需的密鑰（加密密鑰）。

然後，可以將所需的預處理命令用於工作流：

1. 添加和配置 **[!UICONTROL File transfer]** 的子菜單。
1. 添加 **[!UICONTROL Data loading (file)]** 定義檔案格式。
1. 核取 **[!UICONTROL Pre-process the file]** 選項。
1. 指定要應用的預處理命令。
1. 添加其他活動以管理來自檔案的資料。
1. 保存並執行工作流。

在下面的使用案例中給出了一個示例。

**相關主題：**

* [資料載入（檔案）活動](../../workflow/using/data-loading--file-.md)。
* [壓縮或加密檔案](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

## 用例：導入使用控制面板生成的密鑰加密的資料 {#use-case-gpg-decrypt}

在此使用情形中，我們將構建一個工作流，以便使用控制面板中生成的密鑰導入在外部系統中加密的資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用情形的步驟如下：

1. 使用「控制面板」生成密鑰對（公共/專用）。 有關詳細步驟，請參閱 [控制面板文檔](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)。

   * 公鑰將與外部系統共用，外部系統將使用公鑰加密要發送到市場活動的資料。
   * Campaign Classic將使用私鑰解密傳入的加密資料。

   ![](assets/gpg_generate.png)

1. 在外部系統中，使用從控制面板下載的公鑰對要導入到Campaign Classic的資料進行加密。

1. 在Campaign Classic中，構建工作流以導入加密資料並使用通過控制面板安裝的私鑰對其進行解密。 為此，我們將按照以下方式構建工作流：

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 活動：將檔案從外部源傳輸到Campaign Classic。 在本示例中，我們希望從SFTP伺服器傳輸檔案。
   * **[!UICONTROL Data loading (file)]** 活動：將資料從檔案載入到資料庫中，並使用控制面板中生成的私鑰對其進行解密。

1. 開啟 **[!UICONTROL File transfer]** 活動，然後指定要從中導入加密的.gpg檔案的外部帳戶。

   ![](assets/gpg_key_transfer.png)

   有關如何配置活動的全局概念，請參見 [此部分](../../workflow/using/file-transfer.md)。

1. 開啟 **[!UICONTROL Data loading (file)]** 活動，然後根據需要配置。 有關如何配置活動的全局概念，請參見 [此部分](../../workflow/using/data-loading--file-.md)。

   向活動添加預處理階段以解密傳入資料。 要執行此操作，請選擇 **[!UICONTROL Pre-process the file]** 選項，然後複製並貼上此解密命令 **[!UICONTROL Command]** 欄位：

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >在本示例中，我們使用「控制面板」預設使用的密碼，即「密碼短語」。
   >
   >如果您過去通過客戶保護請求在實例上安裝了GPG密鑰，則密碼可能已更改，並且預設情況下與密碼不同。

1. 按一下 **[!UICONTROL OK]** 確認活動配置。

1. 您現在可以運行工作流。 一旦執行，您就可以簽入工作流日誌，該日誌已執行解密，並且已導入檔案中的資料。

   ![](assets/gpg_run.png)

## 教程視頻 {#video}

此視頻顯示如何使用GPG密鑰解密資料。

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

可提供其他Campaign Classic操作視頻 [這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)。
