---
solution: Campaign Classic
product: campaign
title: 如何使用工作流程資料
description: 瞭解如何使用工作流程資料
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 3%

---


# 如何使用工作流程資料{#how-to-use-workflow-data}

## 更新資料庫{#updating-the-database}

所有收集的資料都可用於更新資料庫或傳送。 例如，您可以豐富訊息內容個人化的可能性（包括訊息中的合約數目、指定去年的平均購物車等） 或詳細定位人口（傳送訊息給合約合約持有人、鎖定線上服務的1,000名最佳訂閱者等）。 此資料也可以匯出或封存在清單中。

### 列出和直接更新{#lists-and-direct-updates}

Adobe Campaign資料庫和現有清單的資料可使用兩個專用活動進行更新：

* **[!UICONTROL List update]**&#x200B;活動可讓您將工作表儲存在資料清單中。

   您可以選取現有清單或建立清單。 在這種情況下，將計算名稱和可能的記錄資料夾。

   ![](assets/s_user_create_list.png)

   請參閱[List update](../../workflow/using/list-update.md)。

* **[!UICONTROL Update data]**&#x200B;活動會對資料庫中的欄位執行大量更新。

   有關詳細資訊，請參閱[更新資料](../../workflow/using/update-data.md)。

### 訂閱／取消訂閱管理{#subscription-unsubscription-management}

如需瞭解如何透過工作流程訂閱和取消訂閱資訊服務的收件者，請參閱[訂閱服務](../../workflow/using/subscription-services.md)。

## 透過工作流{#sending-via-a-workflow}傳送

### 傳送活動{#delivery-activity}

傳送活動詳見[傳送](../../workflow/using/delivery.md)。

### 豐富並鎖定遞送{#enriching-and-targeting-deliveries}

傳送可處理工作流程中的資料，以便自訂內容或在目標人口族群選擇的架構中。

例如，在直接郵件傳送的框架內，您可以在抽取檔案中包括從工作流中執行的資料操作中獲取的附加資料：

![](assets/s_advuser_add_data_postal_mail.png)

除了一般的個人化欄位外，您還可以將工作流程階段的個人化欄位新增至傳送內容。 工作流活動中定義的附加資料可以在發送嚮導中保留並使其可訪問，如以下示例所示，用於在直接郵件發送框架中定義輸出檔案的名稱：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的資料由其名稱標識：它一律由&#x200B;**targetData**&#x200B;連結組成。 有關詳細資訊，請參閱[目標資料](../../workflow/using/data-life-cycle.md#target-data)。

在電子郵件傳送的架構中，個人化欄位也可以使用定位工作流程階段中執行之定位擴充功能的資料，如下列範例所示：

![](assets/s_advuser_add_data_email.png)

如果在定位活動中指定區段代碼，則會將其新增至工作流程表格的特定欄，並連同個人化欄位一起提供。 若要顯示所有個人化欄位，請按一下可透過個人化按鈕存取的&#x200B;**[!UICONTROL Target extension > Other...]**&#x200B;連結。

![](assets/s_advuser_segment_code_select.png)

## 匯出資料 {#exporting-data}

### 壓縮或加密檔案{#zipping-or-encrypting-a-file}

Adobe Campaign可讓您匯出壓縮或加密的檔案。 當透過&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活動定義匯出時，您可以定義後置處理，以壓縮或加密檔案。

若要這麼做：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)為實例安裝GPG密鑰對。

   >[!NOTE]
   >
   >控制面板適用於AWS托管的所有客戶（現場托管其行銷實例的客戶除外）。

1. 如果您的Adobe Campaign安裝是由Adobe代管，請聯絡Adobe客戶服務，以便在伺服器上安裝必要的公用程式。
1. 如果您的Adobe Campaign安裝是內部部署，請安裝您要使用的公用程式(例如：GPG、GZIP)以及應用程式伺服器上的必要金鑰（加密金鑰）。

然後，您可以在活動的&#x200B;**[!UICONTROL Script]**&#x200B;標籤或&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動中使用命令或代碼。 在下面的使用案例中提供了示例。

**相關主題：**

* [在處理前解壓縮或解密檔案](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [資料擷取（檔案）活動](../../workflow/using/extraction--file-.md)。

### 使用案例：使用控制面板{#use-case-gpg-encrypt}上安裝的密鑰加密和導出資料

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

1. 開啟&#x200B;**[!UICONTROL File transfer]**&#x200B;活動，然後指定您要傳送檔案的SFTP伺服器。 有關如何配置活動的全局概念，請參閱[本節](../../workflow/using/file-transfer.md)。

   ![](assets/gpg-file-transfer.png)

1. 您現在可以執行工作流程。 執行後，查詢的資料目標將匯出至SFTP伺服器，並匯出至加密的。gpg檔案。

### 教學課程影片{#video}

此視訊說明如何使用GPG金鑰來加密資料，也可在

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

其他Campaign Classic操作視訊可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
