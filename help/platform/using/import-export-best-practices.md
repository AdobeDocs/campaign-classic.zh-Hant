---
solution: Campaign Classic
product: campaign
title: 匯入和匯出最佳實務
description: 進一步瞭解匯入或匯出資料時要遵循的最佳實務。
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 2%

---

# 匯入和匯出最佳實務 {#import-export-best-practices}

謹慎並遵循下面詳述的幾個簡單規則，將有助於確保資料庫內的資料一致性，並避免在資料庫更新或資料匯出期間發生常見錯誤。

## 使用工作流模板{#using-import-templates}

大部份的匯入資料工作流程應包含下列活動：**[!UICONTROL Load file]**、**[!UICONTROL Reconciliation]**、**[!UICONTROL Segmentation]**、**[!UICONTROL Deduplication]**、**[!UICONTROL Update data]**。

使用工作流模板可以非常方便地準備類似的導入並確保資料庫中的資料一致性。

在許多項目中，導入是在沒有&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動的情況下構建的，因為項目中使用的檔案沒有重複項。 有時會從匯入不同的檔案中顯示重複項目。 因此，消除重複就很困難。 因此，重複資料消除步驟是所有導入工作流中的良好預防措施。

切勿假定傳入的資料是一致且正確的，或IT部門或Adobe Campaign主管將負責處理。 在專案期間，請牢記資料清理。 在匯入資料時，可以消除重複資料、進行協調並維持一致性。

[Example：中提供了為導入資料而設計的通用工作流模板的示例。匯入資料](../../platform/using/creating-import-export-templates.md)區段的工作流程範本。

## 使用平面檔案格式{#using-flat-file-formats}

匯入時最有效的格式是平面檔案。 平面檔案可以在資料庫級別以批量模式導入。

例如：

* 分隔符號：制表符或分號
* 首行含標題
* 無字串分隔字元
* 日期格式：YYYY/MM/DD HH:mm:SS

要導入的檔案示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 使用壓縮{#using-compression}

盡可能使用壓縮檔案進行匯入和匯出。 預設支援GZIP。 您可以分別在&#x200B;**[!UICONTROL Load file]**&#x200B;和&#x200B;**[!UICONTROL Extract file]**&#x200B;工作流程活動中，在匯入檔案時新增預處理，或在擷取資料時新增後處理。

**相關主題：**

* [資料載入（檔案）活動](../../workflow/using/data-loading--file-.md)
* [資料擷取（檔案）活動](../../workflow/using/extraction--file-.md)

## 在增量模式下導入{#importing-in-delta-mode}

常規導入必須在delta模式下完成。 這表示每次只會傳送修改或新資料至Adobe Campaign，而非整個表格。

完整匯入應僅用於初始載入。

## 保持一致性{#maintaining-consistency}

為了在Adobe Campaign資料庫中保持資料一致性，請遵循以下原則：

* 如果匯入的資料與Adobe Campaign的參考表格相符，則應與工作流程中的該表格協調。 不應拒絕不符合的記錄。
* 請確定匯入的資料一律是&#x200B;**「已標準化」**（電子郵件、電話號碼、直接郵件位址），且此標準化是可靠的，多年內不會變更。 如果不是這樣，資料庫中可能會出現一些重複項，而Adobe Campaign沒有提供進行「模糊」匹配的工具，因此很難管理和刪除這些重複項。
* 事務性資料應具有協調密鑰，並與現有資料協調以避免建立重複資料。
* **依順序匯入相關檔案**。如果匯入由多個彼此依存的檔案組成，工作流程應確保檔案的匯入順序正確。 檔案失敗時，不會導入其他檔案。
* **匯入資料**&#x200B;時，可以消除重複資料、進行協調並維持一致性。
