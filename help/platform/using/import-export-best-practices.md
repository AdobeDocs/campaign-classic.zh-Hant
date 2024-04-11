---
product: campaign
title: 匯入和匯出最佳實務
description: 進一步瞭解匯入或匯出資料時遵循的最佳實務
feature: Data Management
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 2%

---

# 匯入和匯出最佳實務 {#import-export-best-practices}



請謹慎行事，並遵循下面詳述的幾個簡單規則，有助於確保資料庫內的資料一致性，以及避免在資料庫更新或資料匯出期間發生常見錯誤。

## 使用工作流程範本 {#using-import-templates}

大部分旨在匯入資料的工作流程都應包含下列活動： **[!UICONTROL Load file]**， **[!UICONTROL Reconciliation]**， **[!UICONTROL Segmentation]**， **[!UICONTROL Deduplication]**， **[!UICONTROL Update data]**.

使用工作流程範本可讓您輕鬆準備類似的匯入，並確保資料庫內的資料一致性。

在許多專案中，匯入的建置不包含 **[!UICONTROL Deduplication]** 活動，因為專案中使用的檔案沒有重複專案。 匯入不同檔案時有時會出現重複專案。 因此，去重複化相當困難。 因此，重複資料刪除步驟是所有匯入工作流程中的良好預防措施。

請勿假設傳入的資料一致且正確，或IT部門或Adobe Campaign主管會處理。 在專案期間，請記得要清除資料。 匯入資料時，請進行重複資料刪除、調解及維持一致性。

為匯入資料而設計的一般工作流程範本的範例可在 [範例：匯入資料的工作流程範本](../../platform/using/creating-import-export-templates.md) 區段。

## 使用一般檔案格式 {#using-flat-file-formats}

最有效的匯入格式是平面檔案。 您可以在資料庫層級以大量模式匯入平面檔案。

例如：

* 分隔符號：定位字元或分號
* 帶有標題的第一行
* 無字串分隔符號
* 日期格式： `YYYY/MM/DD HH:mm:SS`

要匯入的檔案範例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 使用壓縮 {#using-compression}

儘可能使用壓縮檔案進行匯入和匯出。 預設支援GZIP。 您可以在匯入檔案時新增前置處理，或在擷取資料時新增後置處理(分別位於 **[!UICONTROL Load file]** 和 **[!UICONTROL Extract file]** 工作流程活動。

**相關主題：**

* [資料載入（檔案）活動](../../workflow/using/data-loading-file.md)
* [資料擷取（檔案）活動](../../workflow/using/extraction-file.md)

## 以差異模式匯入 {#importing-in-delta-mode}

一般匯入必須在差異模式下完成。 這表示只會傳送已修改或新的資料至Adobe Campaign，而非每次都傳送整個表格。

完整匯入僅能用於初始載入。

## 維持一致性 {#maintaining-consistency}

若要維護Adobe Campaign資料庫中資料的一致性，請遵循下列原則：

* 如果匯入的資料符合Adobe Campaign中的參考表格，則應該與工作流程中的該表格進行調解。 應該拒絕不符合的記錄。
* 確保永遠匯入資料 **&quot;normalized&quot;** （電子郵件、電話號碼、直接郵件地址），以及這項標準化是可靠的且不會隨著時間而改變。 若非如此，資料庫中可能會出現一些重複專案，而由於Adobe Campaign未提供執行「模糊」比對的工具，因此將很難管理和移除它們。
* 交易資料應具有調解金鑰，並與現有資料調解，以避免建立重複專案。
* **依序匯入相關檔案**. 如果匯入是由多個彼此相依的檔案所組成，則工作流程應確保檔案以正確的順序匯入。 當檔案失敗時，不會匯入其他檔案。
* **重複資料刪除**、調解及維護匯入資料時的一致性。
