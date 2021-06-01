---
product: campaign
title: 關於自訂收件者表格
description: 關於自訂收件者表格
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---

# 使用自訂收件者表格{#about-custom-recipient-table}

本節詳細說明使用非標準收件者表格的原則。

依預設，Adobe Campaign會提供標準收件者表格，將現成可用的函式和程式連結至該表格。 標準收件者表格包含許多預先定義的欄位和表格，可使用擴充功能表格輕鬆擴充。

如果此擴充方法提供擴充表格的良好彈性，則無法減少表格中的欄位或連結數。 使用非標準表（或「外部收件者表」）可提供更大的靈活性，但在實作時需要某些預防措施。

## 精確度 {#precisions}

此功能可讓Adobe Campaign處理來自外部資料庫的資料：此資料將用作傳送的一組設定檔。 實施此程式需要根據用戶端需求而可能相關的數個精確度。 例如：

* 沒有從Adobe Campaign資料庫到資料流的更新：可通過承載此表的資料庫引擎直接更新表中的資料。
* 在現有資料庫上運行的進程中沒有更改。
* 使用具有非標準結構的配置檔案資料庫：可使用單一例項，以各種結構傳送至儲存在各種表格中的設定檔。
* 更新Adobe Campaign資料庫時不需要任何變更或維護。
* 如果您不需要大多數表欄位，或者資料庫模板未以收件人為中心，則標準收件人表是無用的。
* 若您有大量設定檔，則需要具有少量欄位的表格，才能有效率。 標準收件者表格中有太多欄位供此特定案例使用。

本節說明可讓您映射Adobe Campaign中現有表格的關鍵點，以及要套用以根據任何表格執行傳送的設定。 最後，介紹了如何向用戶提供與標準收件人表可用的介面一樣實用的查詢介面。 要了解本節中介紹的材料，需要對螢幕和方案設計原則有充分的了解。

## Recommendations和限制{#recommendations-and-limitations}

使用外部收件者表格有下列限制：

* Adobe Campaign不支援連結至相同broadlog和/或trackinglog結構的多個收件者結構，也稱為目標結構。 否則，之後資料協調可能會導致異常。

   下圖詳細說明每個自訂收件者架構所需的關係結構：
   ![](assets/custom_recipient_limitation.png)

   我們建議：

   * 將&#x200B;**[!UICONTROL nms:BroadLogRcp]**&#x200B;和&#x200B;**[!UICONTROL nms:TrackingLogRcp]**&#x200B;結構指定至現成可用的&#x200B;**[!UICONTROL nms:Recipientschema]**。 這兩個記錄表不應連結至任何其他自訂收件者表格。
   * 為每個新的自訂收件者結構定義專用的自訂broadlog和追蹤記錄結構。 設定目標對應時，可以自動完成此操作，請參閱[目標對應](../../configuration/using/target-mapping.md)。

* 您無法使用產品中提供的標準&#x200B;**[!UICONTROL Services and Subscriptions]**。

   這表示[此部分](../../delivery/using/managing-subscriptions.md)中詳述的整體操作不適用。

* 與&#x200B;**[!UICONTROL visitor]**&#x200B;表格的連結無法運作。

   因此，要使用&#x200B;**[!UICONTROL Social Marketing]**&#x200B;模組，必須配置儲存步驟以參考正確的表。

   同樣，在使用轉介函式時，必須調整標準初始報文傳輸模板。

* 您無法手動在清單中新增設定檔。

   因此，如果沒有其他配置，[本節](../../platform/using/creating-and-managing-lists.md)中詳述的過程將不適用。

   >[!NOTE]
   >
   >您仍可以使用工作流程建立收件者清單。 有關詳細資訊，請參閱[使用工作流建立配置檔案清單](../../configuration/using/creating-a-profile-list-with-a-workflow.md)。

我們也建議核取不同現成可用設定中使用的預設值：必鬚根據所使用的功能進行若干適應。

例如：

* 某些標準報表，尤其是&#x200B;**Interaction**&#x200B;和&#x200B;**行動應用程式**&#x200B;所提供的報表，必須重新開發。 請參閱[管理報表](../../configuration/using/managing-reports.md)區段。
* 某些工作流程活動的預設設定會參考標準收件者表格(**[!UICONTROL nms:recipient]**):當用於外部收件者表格時，必須變更這些設定。 請參閱[管理工作流程](../../configuration/using/managing-workflows.md)區段。
* 必須調整標準&#x200B;**[!UICONTROL Unsubscription link]**&#x200B;個人化區塊。
* 必須修改標準傳遞範本的目標對應。
* V4表單與外部收件者表格不相容：您必須使用Web應用程式。
