---
title: 關於Adobe Campaign Classic資料模型
description: 本檔案說明Adobe Campaign Classic資料模型的基本概念。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2ce2a1a55e244180a4e62d6f3b5a5ed5bb8aff6e

---


# 關於Campaign Classic資料模型{#about-data-model}

本節說明Adobe Campaign Classic資料模型的基本概念，以便更好地瞭解Campaign內建表格及其互動。

Adobe Campaign資料庫的概念資料模型由一組內建表格及其互動組成。

要訪問每個表的說明，請轉至 **[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選擇資源，然後按一下選 **[!UICONTROL Documentation]** 項卡。

![](assets/data-model_documentation-tab.png)

如需預設「促銷活動傳統資料」模型說明的詳細資訊，請參閱本 [檔案](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html)。

在XML中描述了應用中資料的物理和邏輯結構。 它遵循Adobe Campaign專屬的語法，稱為結構。 如需Adobe Campaign結構描述的詳細資訊，請閱讀本 [節](../../configuration/using/about-schema-reference.md)。

## 概觀 {#data-model-overview}

Adobe Campaign依賴包含連結在一起的表格的關係式資料庫。

Adobe Campaign資料模型的基本結構可說明如下。

## 收件者表格 {#recipient-table}

資料模型依賴於主表，該主表預設為「接收者」表(**NmsRecipient**)。 此表格可儲存所有行銷設定檔。

如需「收件者」表格的詳細資訊，請參閱 [本節](../../configuration/using/default-recipient-table.md)。

## 傳送表格 {#delivery-table}

資料模型也包含專用於儲存所有行銷活動的部分。 通常是「傳送」表(**NmsDelivery**)。 此表中的每個記錄都代表傳送動作或傳送範本。 它包含執行傳送的所有必要參數，例如目標、內容等。

## 日誌表 {#log-tables}

資料模型的另一部分可讓您暫時儲存與促銷活動執行相關的所有記錄檔。

傳送記錄檔是所有通道中傳送給收件者或裝置的所有訊息。 主「傳送日誌」表(**NmsBroadLog**)包含所有收件人的傳送日誌。
主「追蹤記錄檔」表(**NmsTrackingLog**)會儲存所有收件者的追蹤記錄檔。 追蹤記錄是指收件者的反應，例如電子郵件的開信次數和點按次數。 每個反應都對應一個追蹤記錄。
傳送記錄檔和追蹤記錄檔會在特定期間後刪除，此期間會在Adobe Campaign中指定，並可加以修改。 因此，強烈建議您定期匯出記錄檔。

## 技術表 {#technical-tables}

最後，部分資料模型包括用於應用過程的技術資料，包括操作員和用戶權限(**NmsGroup**)、資料夾(**XtkFolder**)。