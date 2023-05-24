---
product: campaign
title: 使用工作流程來匯入和匯出資料
description: 瞭解如何使用Campaign中的工作流程匯入和匯出資料
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 31%

---

# 使用工作流程匯入和匯出資料 {#import-export-workflows}



## 收集資料 {#collecting-data-workflows}

工作流程可以用來自動執行某些匯入過程。無論是從本地檔案還是從 SFTP 匯入資料，都可以使用工作流程來標準化資料管理過程。

### 使用清單中的資料：讀取清單 {#using-data-from-a-list--read-list}

在工作流程中傳送的資料可來自已預先準備資料並建構結構的清單。

此清單可能直接在Adobe Campaign中建立或由匯入 **[!UICONTROL Import a list]** 選項。 如需此選項的詳細資訊，請參閱此 [頁面](../../platform/using/about-generic-imports-exports.md).

如需在工作流程中使用讀取清單活動的詳細資訊，請參閱 [此頁面](../../workflow/using/read-list.md).

### 從檔案載入資料 {#loading-data-from-a-file}

可在工作流程中處理的資料可從結構化檔案中擷取，以便將其匯入Adobe Campaign。

載入資料活動的說明可在以下連結中找到： [資料載入（檔案）](../../workflow/using/data-loading--file-.md) 區段。

要匯入的結構化檔案範例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

收集到資料後，您便可以在工作流程中使用資料，例如擴充傳遞或更新資料庫。 如需詳細資訊，請參閱[此頁面](../../workflow/using/how-to-use-workflow-data.md)。

## 匯出資料 {#exporting-data-via-a-workflow}

在使用可用於轉換資料的一些可用資料管理活動之後，可以使用工作流程來自動執行某些匯出過程或匯出精確資料集。

匯出操作是使用 **[!UICONTROL Data extraction (file) activity]**. 有關如何設定和使用活動的詳細資訊，請參閱 [此頁面](../../workflow/using/extraction--file-.md).
