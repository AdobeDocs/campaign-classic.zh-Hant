---
product: campaign
title: 關於自訂收件者表格
description: 關於自訂收件者表格
feature: Custom Resources
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# 使用自訂收件者表格{#about-custom-recipient-table}

![](../../assets/common.svg)

本節詳細介紹使用自定義（或外部）收件人表的原則。

預設情況下，Adobe Campaign提供一個內置收件表，將開箱即用的功能和進程連結到該表。 內置的接收表具有許多預定義的欄位和表，這些欄位和表可以使用擴展表容易地擴展。

如果此擴展方法提供了擴展表的良好靈活性，則它不允許減少表中的欄位或連結數。 使用非標準表或「外部收件表」允許更大的靈活性，但在實施時需要某些預防措施。

此功能允許Adobe Campaign處理外部資料庫中的資料：此資料將用作一組交貨的配置檔案。 實施此過程涉及一些可能與客戶需求相關的精確度。 例如：

* 沒有與Adobe Campaign資料庫之間的更新流：可以通過承載此表的資料庫引擎直接更新該表中的資料。
* 在現有資料庫上操作的進程中沒有更改。
* 使用具有非標準結構的配置檔案資料庫：使用單個實例將保存在各種結構的表中的配置檔案提交到。
* 更新Adobe Campaign資料庫時不需要更改或維護。
* 如果您不需要大多數表欄位，或者資料庫模板未居中於收件人，則內置的收件人表將無用。
* 為了提高效率，如果配置檔案數量很多，則需要一個欄位少的表。 內置收件人表包含的欄位太多，不適合此特定情況。

本節介紹用於映射Adobe Campaign現有表的關鍵點，以及應用於基於任何表執行交貨的配置。 最後，介紹了如何向用戶提供與內置收件表一樣實用的查詢介面。 要瞭解本節介紹的材料，需要對螢幕和模式設計的原則有充分的瞭解。

## Recommendations和限制 {#recommendations-and-limitations}

使用自定義收件人表具有以下限制：

* Adobe Campaign不支援與同一廣播模式和/或跟蹤日誌模式連結的多個接收方模式，即目標模式。 否則，這可能導致以後資料協調出現異常。

   下圖詳細說明了每個自定義收件人架構所需的關係結構：
   ![](assets/custom_recipient_limitation.png)

   我們建議：

   * 為 **[!UICONTROL nms:BroadLogRcp]** 和 **[!UICONTROL nms:TrackingLogRcp]** 架構到現成 **[!UICONTROL nms:Recipientschema]**。 這兩個日誌表不應連結到任何附加的自定義收件人表。
   * 為每個新自定義收件人架構定義專用自定義廣播和跟蹤日誌架構。 在設定目標映射時可以自動完成此操作，請參見 [目標映射](../../configuration/using/target-mapping.md)。

* 不能使用標準 **[!UICONTROL Services and Subscriptions]** 在產品中提供。

   這意味著在 [此部分](../../delivery/using/managing-subscriptions.md) 不適用。

* 與 **[!UICONTROL visitor]** 表不工作。

   因此，使用 **[!UICONTROL Social Marketing]** 模組必須配置儲存步驟以引用正確的表。

   同樣，在使用引用函式時，必須調整標準初始消息傳送模板。

* 不能在清單中手動添加配置檔案。

   因此，在 [此部分](../../platform/using/creating-and-managing-lists.md) 如果沒有其他配置，則不適用。

   >[!NOTE]
   >
   >您仍然可以使用工作流建立收件人清單。 有關此內容的詳細資訊，請參閱 [使用工作流建立配置檔案清單](../../configuration/using/creating-a-profile-list-with-a-workflow.md)。

我們還建議檢查不同出廠配置中使用的預設值：根據使用的功能，必須進行若干適應。

例如：

* 某些標準報告，特別是 **交互** 和 **移動應用** 必須重新開發。 請參閱 [管理報告](../../configuration/using/managing-reports.md) 的子菜單。
* 某些工作流活動的預設配置引用標準收件人表(**[!UICONTROL nms:recipient]**):這些配置在用於外部收件人表時必須更改。 請參閱 [管理工作流](../../configuration/using/managing-workflows.md) 的子菜單。
* 標準 **[!UICONTROL Unsubscription link]** 必須修改個性化塊。
* 必須修改標準傳遞模板的目標映射。
* V4表單與外部收件人表不相容：必須使用Web應用程式。
