---
product: campaign
title: 開始使用Campaign Classic資料模型
description: 了解如何延伸 Campaign 資料模型、編輯結構描述，以及使用 API 等
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Data Model, Configuration
role: Data Engineer, Developer
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 6%

---

# 開始使用 Campaign 資料模型{#about-data-model}

Adobe Campaign 資料庫的概念資料模型由一組內建表格及其互動組成，本頁面列出主要表格和概念。

## 概覽 {#data-model-overview}

Adobe Campaign仰賴包含連結在一起的表格的關聯式資料庫。 Adobe Campaign資料模型的基本結構描述如下。

### 收件者表格 {#recipient-table}

資料模型仰賴主要表格，預設為收件者表格(**NmsRecipient**)。 此表格可讓您儲存所有行銷設定檔。

有關「收件者」表格的詳細資訊，請參閱 [本節](#default-recipient-table).

### 傳遞表格 {#delivery-table}

資料模型也包含專用於儲存所有行銷活動的零件。 通常是「傳送」表格(**NmsDelivery**)。 此表格中的每一筆記錄代表傳遞動作或傳遞範本。 它包含執行傳遞所需的所有引數，例如目標、內容等。

### 記錄表 {#log-tables}

資料模型的另一個部分可讓您暫時儲存與行銷活動執行相關的所有記錄。

傳遞記錄檔是跨所有通道傳送給收件者或裝置的所有訊息。 主要傳遞記錄表格(**NmsBroadLog**)包含所有收件者的傳遞記錄。
主要追蹤記錄表(**NmsTrackingLog**)會儲存所有收件者的追蹤記錄。 追蹤記錄會參照收件者的回應，例如電子郵件開啟次數和點按次數。 每個回應都會對應至追蹤記錄。
傳送記錄檔和追蹤記錄檔會在特定時段後刪除，該特定時段會在Adobe Campaign中指定並加以修改。 因此，強烈建議您定期匯出記錄檔。

### 技術表格 {#technical-tables}

最後，部分資料模型包含用於應用程式流程的技術資料，包括操作員和使用者許可權(**NmsGroup**)，資料夾(**XtkFolder**)。

## 使用內建的收件者表格 {#default-recipient-table}

Adobe Campaign中的內建收件者表格是建立資料模型的良好起點。 它有許多預先定義的欄位和表格連結，可輕鬆擴充。 當您主要鎖定收件者時，這項功能特別實用，因為適合使用以收件者為中心的簡單資料模型。

使用內建收件者表格的好處如下：

* 使用內建的功能，例如訂閱、種子清單等。
* 提供具有收件者導向資料模型的行銷資料庫。
* 更快速的實作。
* 支援和合作夥伴可輕鬆進行維護。

但是，可以擴充「收件者」表格，但不能減少表格中的欄位或連結數量。

>[!IMPORTANT]
>
>建議不要刪除收件者表格中的欄位（即使這些欄位沒有用），因為這樣可能會導致內建模組中的錯誤。

此外，由於收件者表格是產品的一部分，因此表格及其關聯形式都會隨著產品變更而改變。 因此，需要進行額外維護，以檢查升級時任何擴充功能是否仍然有效。

## 擴充資料模型 {#extending-data-model}

開始使用Adobe Campaign時，您需要評估預設資料模型，以檢查哪個表格最適合儲存行銷資料。

如果相關，您可以將預設收件者表格與現成可用的欄位搭配使用，如中所述 [本節](#default-recipient-table).

如有需要，您可以使用兩種機制來擴充它：

* 使用新欄位擴充現有表格。 例如，您可以新增「忠誠度」欄位至「收件者」表格。
* 建立新表格（例如「購買」表格），列出資料庫中每個設定檔進行的所有購買，並將其連結至收件者表格。

如需設定擴充功能綱要以擴充概念資料模型的詳細資訊，請參閱 [關於綱要版本](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>資料模型擴充功能會保留給進階使用者。

## 使用自訂收件者表格 {#custom-recipient-table}

設計Adobe Campaign資料模型時，您可以使用 [內建收件者表格](#default-recipient-table)，或決定建立 [自訂收件者表格](../../configuration/using/about-custom-recipient-table.md) 儲存行銷設定檔的表格。

事實上，如果您的資料模型不符合收件者導向的結構，您可以在Adobe Campaign中設定其他表格作為目標維度。 例如，當您需要將目標定位為家庭、帳戶（例如行動電話）和公司/網站時，這可能相關，而不僅僅是收件者。

>[!NOTE]
>
>在此情況下，您需要建立新的 [目標對應](../../configuration/using/target-mapping.md).

有關使用自訂收件者表格時所需的所有原則和步驟詳情，請參閱 [本節](../../configuration/using/about-custom-recipient-table.md).

使用自訂收件者表格的好處如下：

* **彈性的資料模型**  — 如果您不需要大部分的收件者表格欄位，或資料模型不是以收件者為中心，內建的收件者表格就毫無用處。

* **擴充性**  — 大型磁碟區需要精簡的表格，且只有幾個欄位，才能有效率地設計。 內建的收件者表格會有太多無用的欄位，這可能會影響效能並缺乏效率。

* **資料位置**  — 如果資料位於外部現有的行銷資料庫，則使用內建的收件者表格時可能需要花費太多時間。 根據現有結構建立新結構比較簡單。

* **輕鬆移轉**  — 不需要進行維護即可檢查升級時所有擴充功能是否仍然有效。

>[!IMPORTANT]
>
>進階使用者可以保留使用自訂收件者表格，且會受一些限制。 如需詳細資訊，請參閱[本節](../../configuration/using/about-custom-recipient-table.md)。

## 相關主題

在以下章節中進一步瞭解Campaign資料模型：

* **主要表格的說明**  — 如需預設Campaign Classic資料模型說明的詳細資訊，請參閱 [本節](../../configuration/using/data-model-description.md).

* **每個表格的完整說明**  — 若要存取每個表格的完整說明，請前往 **[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選取資源，然後按一下 **[!UICONTROL Documentation]** 標籤。

  ![](assets/data-model_documentation-tab.png)


* **行銷活動綱要**  — 以XML描述應用程式中資料的實體和邏輯結構。 並且遵循 Adobe Campaign 專屬的語法，稱為綱要 (schema)。如需有關Adobe Campaign綱要的詳細資訊，請閱讀 [本節](../../configuration/using/about-schema-reference.md).

* **資料模型最佳實務**  — 在中瞭解Campaign資料模型架構和相關最佳實務 [本節](../../configuration/using/data-model-best-practices.md#data-model-architecture).
