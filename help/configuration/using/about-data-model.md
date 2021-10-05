---
product: campaign
title: 開始使用Campaign Classic資料模型
description: 了解如何延伸 Campaign 資料模型、編輯結構描述，以及使用 API 等
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# 開始使用 Campaign 資料模型{#about-data-model}

![](../../assets/v7-only.svg)

Adobe Campaign 資料庫的概念資料模型由一組內建表格及其互動組成，本頁面列出主要表格和概念。

## 概覽 {#data-model-overview}

Adobe Campaign依賴包含連結在一起之表的關係資料庫。 Adobe Campaign資料模型的基本結構描述如下。

### 收件者表格 {#recipient-table}

資料模型依賴於主表，該主表預設為收件者表(**NmsRecipient**)。 此表格可讓儲存所有行銷設定檔。

如需「收件者」表格的詳細資訊，請參閱[此區段](#default-recipient-table)。

### 傳送表格 {#delivery-table}

資料模型也包含專用於儲存所有行銷活動的部分。 通常是傳送表格(**NmsDelivery**)。 此表中的每個記錄都表示傳遞操作或傳遞模板。 它包含執行傳送所需的所有必要參數，例如目標、內容等。

### 記錄表 {#log-tables}

資料模型的另一個部分可讓您暫時儲存與執行促銷活動相關聯的所有記錄。

傳送記錄是所有通道上傳送給收件者或裝置的所有訊息。 主要傳送記錄表(**NmsBroadLog**)包含所有收件者的傳送記錄。
主要追蹤記錄表(**NmsTrackingLog**)儲存所有收件者的追蹤記錄。 追蹤記錄會參考收件者的反應，例如電子郵件開啟次數和點按次數。 每個反應都對應至追蹤記錄。
傳送記錄檔和追蹤記錄檔會在特定時段後刪除，而特定時段會在Adobe Campaign中指定，且可以修改。 因此，強烈建議定期匯出日誌。

### 技術表 {#technical-tables}

最後，資料模型的一部分包含用於應用程式的技術資料，包括運算子和用戶權限(**NmsGroup**)、資料夾(**XtkFolder**)。

## 使用內建的收件者表格 {#default-recipient-table}

Adobe Campaign中的內建收件者表格是建立資料模型的好起點。 它有許多預先定義的欄位和表格連結，可輕鬆擴充。 當您主要鎖定收件者時，這項功能特別實用，因為它適合簡單的收件者導向資料模型。

使用內建收件者表格的優點如下：

* 使用內建功能（例如訂閱、種子清單等）。
* 以收件者為中心的資料模型提供行銷資料庫。
* 更快速的實作。
* 由支援和合作夥伴輕鬆維護。

不過，您可以擴充「收件者」表格，但不能減少表格中的欄位或連結數。

>[!IMPORTANT]
>
>建議不要刪除收件者表格中的欄位（即使這些欄位毫無用處），因為這可能會在內建模組中導致錯誤。

此外，由於「收件者」表格是產品的一部分，因此表格及其關聯表單都會隨著產品變更而改變。 因此，需要額外的維護，以檢查升級時是否有任何擴充功能仍有效。

## 擴充資料模型 {#extending-data-model}

從Adobe Campaign開始，您需要評估預設資料模型，以檢查哪個表格最適合儲存行銷資料。

若相關，您可以使用預設的收件者表格搭配現成欄位，例如[此區段](#default-recipient-table)中所述。

如有需要，您可使用兩種機制來擴充：

* 使用新欄位擴展現有表。 例如，您可以將新的「忠誠度」欄位新增至「收件者」表格。
* 建立新表，例如「購買」表，列出資料庫的每個配置檔案進行的所有購買，並將其連結到「收件人」表。

有關配置擴展架構以擴展概念資料模型的詳細資訊，請參閱[關於架構版本](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>擴充資料模型會保留給進階使用者。

## 使用自訂收件者表格 {#custom-recipient-table}

在設計Adobe Campaign資料模型時，您可以使用[現成可用的收件者表格](#default-recipient-table)，或決定建立[自訂收件者表格](../../configuration/using/about-custom-recipient-table.md)以儲存您的行銷設定檔。

事實上，如果您的資料模型不符合收件者為中心的結構，您可以在Adobe Campaign中將其他表格設為目標維度。 例如，當您需要鎖定家庭、帳戶（如行動電話）和公司/網站，而非單純的收件者時，這可能相關。

>[!NOTE]
>
>在這種情況下，您需要建立新的[目標映射](../../configuration/using/target-mapping.md)。

使用自訂收件者表格時，所需的所有原則和步驟在[本節](../../configuration/using/about-custom-recipient-table.md)中詳細說明。

使用自訂收件者表格的優點如下：

* **彈性的資料模型**  — 如果您不需要大部分的收件者表格欄位，或資料模型並非以收件者為中心，現成可用的收件者表格將毫無用處。

* **可擴充性**  — 大卷需要精簡的表格，其中只有幾個欄位，才能實現高效的設計。現成可用的收件者表格會有太多無用的欄位，這可能會影響效能並且缺乏效率。

* **資料位置**  — 如果資料位於外部現有行銷資料庫，則使用現成可用的收件者表格可能需花費太多精力。根據現有結構建立新結構比較簡單。

* **輕鬆移轉**  — 無需維護即可檢查所有擴充功能在升級時是否仍有效。

>[!IMPORTANT]
>
>使用自訂收件者表格會保留給進階使用者，且會受到一些限制。 如需詳細資訊，請參閱[本節](../../configuration/using/about-custom-recipient-table.md)。

## 相關主題

在以下小節中進一步了解Campaign資料模型：

* **主要表格的說明**  — 如需預設Campaign Classic資料模型說明的詳細資訊，請參閱 [本區段](../../configuration/using/data-model-description.md)。

* **每個表格的完整說明**  — 若要存取每個表格的完整說明，請前往 **[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選取資源，然後按一下 **[!UICONTROL Documentation]** 索引標籤。

   ![](assets/data-model_documentation-tab.png)


* **促銷活動結構**  — 應用程式中所攜帶資料的物理和邏輯結構以XML描述。並且遵循 Adobe Campaign 專屬的語法，稱為綱要 (schema)。如需Adobe Campaign結構的詳細資訊，請閱讀[本區段](../../configuration/using/about-schema-reference.md)。

* **資料模型最佳實務**  — 在本小節中了解Campaign資料模型架構和相關 [最佳實務](../../configuration/using/data-model-best-practices.md#data-model-architecture)。
