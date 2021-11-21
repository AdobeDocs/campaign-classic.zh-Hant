---
product: campaign
title: 使用工作流程來匯入和匯出資料
description: 了解如何使用Campaign Classic中的工作流程匯入和匯出資料。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 31%

---

# 使用工作流程匯入和匯出資料 {#import-export-workflows}

![](../../assets/common.svg)

## 收集資料 {#collecting-data-workflows}

工作流程可以用來自動執行某些匯入過程。無論是從本地檔案還是從 SFTP 匯入資料，都可以使用工作流程來標準化資料管理過程。

### 使用清單中的資料：讀取清單 {#using-data-from-a-list--read-list}

在工作流程中傳送的資料可來自清單，據此資料已預先準備並結構化。

此清單可能是直接在Adobe Campaign中建立，或由 **[!UICONTROL Import a list]** 選項。 如需此選項的詳細資訊，請參閱 [頁面](../../platform/using/about-generic-imports-exports.md).

如需在工作流程中使用讀取清單活動的詳細資訊，請參閱 [本頁](../../workflow/using/read-list.md).

### 從檔案載入資料 {#loading-data-from-a-file}

工作流程中處理的資料可從結構化檔案中擷取，以便匯入至Adobe Campaign。

載入資料活動的說明位於 [資料載入（檔案）](../../workflow/using/data-loading--file-.md) 區段。

要匯入的結構化檔案範例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

收集完資料後，您就可以在工作流程中使用資料，例如擴充傳送或更新資料庫。 如需詳細資訊，請參閱[此頁面](../../workflow/using/how-to-use-workflow-data.md)。

## 匯出資料 {#exporting-data-via-a-workflow}

在使用可用於轉換資料的一些可用資料管理活動之後，可以使用工作流程來自動執行某些匯出過程或匯出精確資料集。

導出操作使用 **[!UICONTROL Data extraction (file) activity]**. 如需如何設定和使用活動的詳細資訊，請參閱 [本頁](../../workflow/using/extraction--file-.md).
