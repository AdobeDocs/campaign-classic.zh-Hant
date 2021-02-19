---
solution: Campaign Classic
product: campaign
title: 關於自訂收件者表格
description: 關於自訂收件者表格
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 2%

---


# 關於自訂收件者表格{#about-custom-recipient-table}

本節詳細說明使用非標準收件者表的原則。

依預設，Adobe Campaign會提供標準的收件者表格，現成可用的函式和程式會連結到該表格。 標準接收表具有許多預定義的欄位和表，可以使用擴展表輕鬆擴展。

如果此擴充方法提供擴充表格的良好彈性，則不允許減少表格中的欄位或連結數。 使用非標準表（或「外部收件者表」）可提供更大的靈活性，但在實施時需要某些預防措施。

## 精度{#precisions}

此功能可讓Adobe Campaign處理來自外部資料庫的資料：此資料將用作一組傳送的描述檔。 實施此程式涉及多項可能與客戶需求相關的精確度。 例如：

* 沒有Adobe Campaign資料庫的更新串流：此表中的資料可以通過托管該表的資料庫引擎直接更新。
* 對在現有資料庫上運行的進程沒有更改。
* 使用具有非標準結構的配置檔案資料庫：使用單個實例，將檔案傳遞到保存在各種結構的表中。
* 更新Adobe Campaign資料庫時，不需要進行變更或維護。
* 如果您不需要大部分的表格欄位，或者資料庫範本未置於收件者的正中，標準收件者表格將無用。
* 為了提高效率，如果配置檔案數量很大，則需要一個欄位數很少的表。 標準收件者表格中的欄位太多，無法處理此特定案例。

本節說明可讓您映射Adobe Campaign中現有表格的關鍵點，以及套用以根據任何表格執行傳送的設定。 最後，說明如何像標準收件人表格一樣，向用戶提供查詢介面。 為了瞭解本節中介紹的內容，您必須熟悉螢幕和架構設計的原則。

## 建議與限制{#recommendations-and-limitations}

使用外部收件者表格有下列限制：

* Adobe Campaign不支援連結至相同廣播和／或追蹤記錄結構的多個收件者結構描述，稱為定位結構描述。 否則，在事後的資料協調中可能會出現異常。

   下圖詳細說明每個自訂收件者架構所需的關係結構：
   ![](assets/custom_recipient_limitation.png)

   我們建議：

   * 將&#x200B;**[!UICONTROL nms:BroadLogRcp]**&#x200B;和&#x200B;**[!UICONTROL nms:TrackingLogRcp]**&#x200B;方案指定到現成可用的&#x200B;**[!UICONTROL nms:Recipientschema]**。 這兩個日誌表不應連結到任何其他自定義收件人表。
   * 為每個新的自訂收件者架構定義專用的自訂廣告和追蹤記錄結構。 在設定目標映射時，可以自動完成此操作，請參閱[目標映射](../../configuration/using/target-mapping.md)。

* 您無法使用產品中提供的標準&#x200B;**[!UICONTROL Services and Subscriptions]**。

   這表示[本節](../../delivery/using/managing-subscriptions.md)中詳述的整體操作不適用。

* 與&#x200B;**[!UICONTROL visitor]**&#x200B;表格的連結無法運作。

   因此，要使用&#x200B;**[!UICONTROL Social Marketing]**&#x200B;模組，必須配置儲存步驟以引用正確的表。

   同樣地，在使用轉介功能時，必須調整標準的初始訊息傳送範本。

* 您無法手動在清單中新增描述檔。

   因此，如果沒有額外的配置，則[本節](../../platform/using/creating-and-managing-lists.md)中詳細介紹的過程不適用。

   >[!NOTE]
   >
   >您仍然可以使用工作流程來建立收件者清單。 有關詳細資訊，請參閱[使用工作流建立配置式清單。](../../configuration/using/creating-a-profile-list-with-a-workflow.md)

我們也建議檢查不同現成可用組態所使用的預設值：根據使用的功能，必須進行若干適應。

例如：

* 某些標準報表，尤其是&#x200B;**Interaction**&#x200B;和&#x200B;**Mobile Applications**&#x200B;所提供的報表，必須重新開發。 請參閱[管理報表](../../configuration/using/managing-reports.md)一節。
* 某些工作流活動的預設配置引用標準收件人表(**[!UICONTROL nms:recipient]**):這些配置在用於外部收件者表時必須更改。 請參閱[管理工作流程](../../configuration/using/managing-workflows.md)一節。
* 標準&#x200B;**[!UICONTROL Unsubscription link]**&#x200B;個人化區塊必須調整。
* 必須修改標準傳送範本的目標對應。
* V4表格與外部收件者表格不相容：您必須使用Web應用程式。

