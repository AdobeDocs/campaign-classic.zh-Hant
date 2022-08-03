---
product: campaign
title: 開始使用Campaign Classic資料模型
description: 了解如何延伸 Campaign 資料模型、編輯結構描述，以及使用 API 等
feature: Data Model
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# 開始使用 Campaign 資料模型{#about-data-model}

![](../../assets/v7-only.svg)

Adobe Campaign 資料庫的概念資料模型由一組內建表格及其互動組成，主表和概念列在此頁中。

## 概覽 {#data-model-overview}

Adobe Campaign依賴於一個關係資料庫，該資料庫包含連結在一起的表。 Adobe Campaign資料模型的基本結構如下：

### 收件人表 {#recipient-table}

資料模型依賴於主表，該主表預設為收件人表(**Nms收件人**)。 此表用於儲存所有市場營銷配置檔案。

有關「收件人」(Recipient)表格的詳細資訊，請參見 [此部分](#default-recipient-table)。

### 交貨表 {#delivery-table}

資料模型還包括專用於儲存所有營銷活動的部件。 通常是Delivery表(**Nms交付**)。 此表中的每個記錄都表示交貨操作或交貨模板。 它包含執行遞送所需的所有參數，如目標、內容等。

### 日誌表 {#log-tables}

資料模型的另一部分允許臨時儲存與市場活動的執行相關聯的所有日誌。

傳遞日誌是所有通道中發送給收件人或設備的所有消息。 主傳遞日誌表(**NmsBroadLog**)包含所有收件人的傳遞日誌。
主跟蹤日誌表(**Nms跟蹤日誌**)儲存所有收件人的跟蹤日誌。 跟蹤日誌是指收件人的反應，如電子郵件的開啟和點擊。 每個反應都對應於跟蹤日誌。
交貨日誌和跟蹤日誌在特定時間段後被刪除，該時間段在Adobe Campaign指定，可以修改。 因此，強烈建議定期導出日誌。

### 技術表 {#technical-tables}

最後，部分資料模型包括用於應用程式的技術資料，包括操作員和用戶權限(**NMS組**)，資料夾(**Xtk資料夾**)。

## 使用內置收件人表 {#default-recipient-table}

Adobe Campaign的內置收件人表為構建資料模型提供了良好的起點。 它具有許多可輕鬆擴展的預定義欄位和表連結。 當您主要針對收件人時，此功能特別有用，因為它適合以收件人為中心的簡單資料模型。

使用內置收件人表的好處如下：

* 使用訂閱、種子清單等功能內置。
* 提供具有以收件人為中心的資料模型的市場營銷資料庫。
* 加快實施。
* 支援和合作夥伴可輕鬆維護。

但是，可以擴展「收件人」表，但不能減少表中的欄位或連結數。

>[!IMPORTANT]
>
>建議不要刪除收件人表中的欄位（即使這些欄位無用），因為這可能會導致內置模組中的錯誤。

此外，由於「收件人」(Recipient)表格是產品的一部分，因此表格及其關聯表格都會隨著產品的變化而變化。 因此，需要額外的維護，以檢查升級時是否仍有效。

## 擴展資料模型 {#extending-data-model}

從Adobe Campaign開始，您需要評估預設資料模型，以檢查哪個表最適合儲存您的營銷資料。

如果相關，可將預設的「收件人」表與現成欄位一起使用，如中所述 [此部分](#default-recipient-table)。

如果需要，可以使用兩種機制擴展它：

* 用新欄位擴展現有表。 例如，您可以向「收件人」表添加新的「會員」欄位。
* 建立新表，例如，列出資料庫每個配置檔案所做的所有採購的「採購」表，並將其連結到「收件人」表。

有關配置擴展架構以擴展概念資料模型的詳細資訊，請參見 [關於架構版本](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>擴展資料模型是為高級用戶保留的。

## 使用自定義收件人表 {#custom-recipient-table}

在設計Adobe Campaign資料模型時，可使用 [內置收件人表](#default-recipient-table)，或決定建立 [自定義收件人表](../../configuration/using/about-custom-recipient-table.md) 用於儲存市場營銷概要檔案的表。

實際上，如果資料模型不適合以收件人為中心的結構，則可以將其他表設定為Adobe Campaign內的目標維。 例如，當您需要將目標對準家庭、帳戶（如手機）和公司/站點，而不是單純的接收者時，這可能是相關的。

>[!NOTE]
>
>在這種情況下，您需要建立 [目標映射](../../configuration/using/target-mapping.md)。

使用自定義收件人表時需要的所有原則和步驟在中詳細介紹 [此部分](../../configuration/using/about-custom-recipient-table.md)。

使用自定義收件人表的好處如下：

* **靈活的資料模型**  — 如果您不需要大多數「收件人」表欄位，或者資料模型不是以收件人為中心，則內置的收件人表是無用的。

* **可擴充性**  — 大型卷需要精簡的表格，而欄位很少，以便進行高效設計。 內置的收件人表將包含太多無用欄位，這可能影響效能並且缺乏效率。

* **資料位置**  — 如果資料駐留在外部現有的市場營銷資料庫上，則使用內置收件表可能需要付出太多努力。 基於現有結構建立新結構更簡單。

* **輕鬆遷移**  — 無需維護即可檢查所有擴展在升級時是否仍然有效。

>[!IMPORTANT]
>
>使用自定義收件人表是為高級用戶保留的，並受到一些限制。 如需詳細資訊，請參閱[本節](../../configuration/using/about-custom-recipient-table.md)。

## 相關主題

在以下各節中瞭解有關市場活動資料模型的詳細資訊：

* **主表的說明**  — 有關預設Campaign Classic資料模型說明的詳細資訊，請參閱 [此部分](../../configuration/using/data-model-description.md)。

* **每個表的完整說明**  — 要訪問每個表的完整說明，請轉到 **[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選擇資源，然後按一下 **[!UICONTROL Documentation]** 頁籤。

   ![](assets/data-model_documentation-tab.png)


* **市場活動架構**  — 應用程式中所承載資料的物理和邏輯結構用XML描述。 並且遵循 Adobe Campaign 專屬的語法，稱為綱要 (schema)。有關Adobe Campaign架構的詳細資訊，請閱讀 [此部分](../../configuration/using/about-schema-reference.md)。

* **資料模型最佳做法**  — 瞭解市場活動資料模型體系結構和相關最佳實踐， [此部分](../../configuration/using/data-model-best-practices.md#data-model-architecture)。
