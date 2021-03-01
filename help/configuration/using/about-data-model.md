---
solution: Campaign Classic
product: campaign
title: 開始使用Campaign Classic資料模型
description: 了解如何延伸 Campaign 資料模型、編輯結構描述，以及使用 API 等
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 6%

---


# 開始使用 Campaign 資料模型{#about-data-model}

Adobe Campaign 資料庫的概念資料模型由一組內建表格及其互動組成，本頁列出了主表和概念。

## 概觀 {#data-model-overview}

Adobe Campaign依賴於一個關係資料庫，該資料庫包含連結在一起的表。 Adobe Campaign資料模型的基本結構可以描述如下：

### 收件者表{#recipient-table}

資料模型依賴於主表，該主表預設為「接收者」表(**NmsRecipient**)。 此表格可儲存所有行銷設定檔。

有關「收件人」(Recipient)表格的詳細資訊，請參閱[本節](#default-recipient-table)。

### 傳送表{#delivery-table}

資料模型也包含專用於儲存所有行銷活動的部分。 通常它是「傳送」表(**NmsDelivery**)。 此表中的每個記錄都代表傳送動作或傳送範本。 它包含執行傳送的所有必要參數，例如目標、內容等。

### 記錄表{#log-tables}

資料模型的另一部分可讓您暫時儲存與促銷活動執行相關的所有記錄檔。

傳送記錄檔是所有通道中傳送給收件者或裝置的所有訊息。 主「傳送日誌」表(**NmsBroadLog**)包含所有接收者的傳送日誌。
主「追蹤記錄檔」表(**NmsTrackingLog**)儲存所有收件者的追蹤記錄檔。 追蹤記錄是指收件者的反應，例如電子郵件的開信次數和點按次數。 每個反應都對應一個追蹤記錄。
傳送記錄檔和追蹤記錄檔會在特定期間後刪除，此期間在Adobe Campaign指定並可加以修改。 因此，強烈建議您定期匯出記錄檔。

### 技術表{#technical-tables}

最後，部分資料模型包含用於應用程式的技術資料，包括操作員和用戶權限(**NmsGroup**)、資料夾(**XtkFolder**)。

## 使用預設的Recipient表{#default-recipient-table}

Adobe Campaign的現成可用「收件者」表為您建立資料模型提供了良好的起點。 它有許多預先定義的欄位和表格連結，可輕鬆擴充。 當您主要針對收件者時，這特別有用，因為它適合簡單的收件者導向資料模型。

使用標準「收件者」(Recipient)表的優點如下：

* 立即可用的功能，例如訂閱、種子清單、調查、社交等。
* 提供以收件者為中心的資料模型為行銷資料庫。
* 更快速的實作。
* 由支援和合作夥伴輕鬆維護。

但是，可以擴展「收件人」(Recipient)表，但不能減少表中的欄位或連結數。

>[!IMPORTANT]
>
>建議不要刪除收件者表格中的欄位（即使欄位無用），因為這可能會導致內建模組發生錯誤。

此外，由於「收件者」(Recipient)表格是產品的一部分，因此表格及其關聯表格都會隨著產品的變更而改變。 因此，需要額外的維護功能，才能檢查升級時是否仍有任何擴充功能。

## 擴展資料模型{#extending-data-model}

從Adobe Campaign開始，您需要評估預設資料模型，以檢查哪個表格最適合儲存行銷資料。

如果相關，您可以使用預設的「收件者」表格和現成可用的欄位，如[本節](#default-recipient-table)所述。

如有需要，您可以使用兩種機制來擴充它：

* 使用新欄位擴充現有表格。 例如，您可以在「收件者」表格中新增「忠誠度」欄位。
* 建立新表格，例如列出資料庫每個描述檔所有購買項目的「購買」表格，並將其連結至「收件者」表格。

有關配置擴展模式以擴展概念資料模型的詳細資訊，請參見[關於模式版本](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>擴充資料模型會保留給進階使用者。

## 使用自訂收件者表{#custom-recipient-table}

在設計您的Adobe Campaign資料模型時，您可以使用[現成可用的收件者表](#default-recipient-table)，或決定建立[自訂收件者表](../../configuration/using/about-custom-recipient-table.md)表格來儲存您的行銷描述檔。

事實上，如果您的資料模型不符合以收件者為中心的結構，您可以在Adobe Campaign內將其他表格設定為定位維度。 例如，當您需要鎖定家庭、帳戶（如行動電話）和公司／網站（而不只是收件者）時，這可能是相關的。

>[!NOTE]
>
>在這種情況下，您需要建立新的[目標映射](../../configuration/using/target-mapping.md)。

使用自訂收件者表格時，所需的原則和步驟詳見[本節](../../configuration/using/about-custom-recipient-table.md)。

使用自訂「收件者」表格的優點如下：

* **彈性的資料模型** -如果您不需要大部分的「收件者」表格欄位，或者資料模型並非以收件者為中心，即裝即用的「收件者」表格是無用的。

* **可擴充性** -大卷需要簡化的表格，而且欄位很少，以便高效設計。現成可用的「收件者」表格中會有太多無用的欄位，這可能會影響效能並降低效率。

* **資料位置** -如果資料位於外部現有的行銷資料庫，使用現成可用的「收件者」表格可能會耗費太多精力。建立以現有結構為基礎的新結構更簡單。

* **輕鬆移轉** -不需要維護，即可檢查所有擴充功能是否在升級時仍然有效。

>[!IMPORTANT]
>
>使用自訂收件者表格會保留給進階使用者，並受到一些限制。 如需詳細資訊，請參閱[本節](../../configuration/using/about-custom-recipient-table.md)。

## 相關主題

進一步瞭解以下章節中的促銷活動資料模型：

* **主表的說明** -有關預設Campaign Classic資料模型說明的詳細資訊，請參 [閱本節](../../configuration/using/data-model-description.md)。

* **每個表的完整說明** -要訪問每個表的完整說明，請轉至 **[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選擇一個資源，然後按一下該選 **[!UICONTROL Documentation]** 項卡。

   ![](assets/data-model_documentation-tab.png)


* **促銷活動結構** -應用程式中所載資料的物理和邏輯結構，以XML來描述。並且遵循 Adobe Campaign 專屬的語法，稱為綱要 (schema)。有關Adobe Campaign方案的詳細資訊，請讀取[本節](../../configuration/using/about-schema-reference.md)。

* **資料模型最佳實務** -在本節中瞭解Campaign資料模型架構和相關的最 [佳實務](../../configuration/using/data-model-best-practices.md#data-model-architecture)。
