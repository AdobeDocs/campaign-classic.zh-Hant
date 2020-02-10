---
title: 如何使用工作流程資料
seo-title: 如何使用工作流程資料
description: 如何使用工作流程資料
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 如何使用工作流程資料{#how-to-use-workflow-data}

## 更新資料庫 {#updating-the-database}

所有收集的資料都可用於更新資料庫或傳送。 例如，您可以豐富訊息內容個人化的可能性（包括訊息中的合約數目、指定去年的平均購物車等）或詳細定位人口（傳送訊息給合約合約持有人、鎖定線上服務的1,000名最佳訂閱者等）。 此資料也可以匯出或封存在清單中。

### 清單和直接更新 {#lists-and-direct-updates}

Adobe Campaign資料庫和現有清單的資料可使用兩個專用活動進行更新：

* 此活 **[!UICONTROL List update]** 動可讓您將工作表儲存在資料清單中。

   您可以選取現有清單或建立清單。 在這種情況下，將計算名稱和可能的記錄資料夾。

   ![](assets/s_user_create_list.png)

   請參閱清 [單更新](../../workflow/using/list-update.md)。

* 活 **[!UICONTROL Update data]** 動會對資料庫中的欄位執行大量更新。

   For more on this, refer to [Update data](../../workflow/using/update-data.md).

### 訂閱／取消訂閱管理 {#subscription-unsubscription-management}

如需透過工作流程訂閱和取消訂閱資訊服務的收件者，請參閱訂閱 [服務](../../workflow/using/subscription-services.md)。

## 透過工作流程傳送 {#sending-via-a-workflow}

### 傳送活動 {#delivery-activity}

傳送活動在「傳送」中詳 [細說明](../../workflow/using/delivery.md)。

### 豐富和鎖定遞送 {#enriching-and-targeting-deliveries}

傳送可處理工作流程中的資料，以便自訂內容或在目標人口族群選擇的架構中。

例如，在直接郵件傳送的框架內，您可以在抽取檔案中包括從工作流中執行的資料操作中獲取的附加資料：

![](assets/s_advuser_add_data_postal_mail.png)

除了一般的個人化欄位外，您還可以將工作流程階段的個人化欄位新增至傳送內容。 工作流活動中定義的附加資料可以在發送嚮導中保留並使其可訪問，如以下示例所示，用於在直接郵件發送框架中定義輸出檔案的名稱：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的資料由其名稱標識：它一律由targetData連 **結組成** 。 For more on this, refer to [Target data](../../workflow/using/executing-a-workflow.md#target-data).

在電子郵件傳送的架構中，個人化欄位也可以使用目標擴充功能在目標工作流程階段中執行的資料，如下例所示：

![](assets/s_advuser_add_data_email.png)

如果在定位活動中指定區段代碼，則會將其新增至工作流程表格的特定欄，並連同個人化欄位一起提供。 若要顯示所有個人化欄位，請按一下可 **[!UICONTROL Target extension > Other...]** 透過個人化按鈕存取的連結。

![](assets/s_advuser_segment_code_select.png)

## 匯出資料 {#exporting-data}

### 壓縮或加密檔案 {#zipping-or-encrypting-a-file}

Adobe Campaign可讓您匯出壓縮或加密的檔案。 當透過活動定義匯 **[!UICONTROL Data extraction (file)]** 出時，您可以定義後置處理來壓縮或加密檔案。

若要這麼做：

* 如果您的Adobe Campaign安裝是由Adobe代管：向Support(支 [持](https://support.neolane.net) )發送請求，要求在伺服器上安裝必要的實用程式。
* 如果您的Adobe Campaign安裝是在現場進行：安裝您要使用的實用程式(例如：GPG、GZIP)以及應用程式伺服器上的必要金鑰（加密金鑰）。

然後，您可以使用命令或程式碼，例如：

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

導入檔案時，也可以解壓縮或解密檔案。 請參 [閱在處理前解壓縮或解密檔案](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)。
