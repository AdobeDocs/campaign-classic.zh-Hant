---
solution: Campaign Classic
product: campaign
title: 使用工作流程來匯入和匯出資料
description: 瞭解如何使用Campaign Classic中的工作流程匯入和匯出資料。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 31%

---


# 使用工作流程{#import-export-workflows}匯入和匯出資料

## 收集資料{#collecting-data-workflows}

工作流程可以用來自動執行某些匯入過程。無論是從本地檔案還是從 SFTP 匯入資料，都可以使用工作流程來標準化資料管理過程。

### 使用清單中的資料：讀取清單{#using-data-from-a-list--read-list}

在工作流中發送的資料可以來自清單，其中資料已事先準備並結構化。

此清單可能是直接在Adobe Campaign建立的，或由&#x200B;**[!UICONTROL Import a list]**&#x200B;選項導入的。 有關此選項的詳細資訊，請參閱此[頁](../../platform/using/about-generic-imports-exports.md)。

有關在工作流中使用讀清單活動的詳細資訊，請參閱[此頁](../../workflow/using/read-list.md)。

### 從檔案{#loading-data-from-a-file}載入資料

在工作流中處理的資料可以從結構化檔案中提取，以便可以導入到Adobe Campaign。

在[資料載入（檔案）](../../workflow/using/data-loading--file-.md)區段中可找到載入資料活動的說明。

要導入的結構化檔案示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

收集到資料後，您就可以在工作流程中使用資料，例如豐富傳送內容或更新資料庫。 有關詳細資訊，請參見[此頁面](../../workflow/using/how-to-use-workflow-data.md)。

## 匯出資料{#exporting-data-via-a-workflow}

在使用可用於轉換資料的一些可用資料管理活動之後，可以使用工作流程來自動執行某些匯出過程或匯出精確資料集。

導出操作使用&#x200B;**[!UICONTROL Data extraction (file) activity]**&#x200B;執行。 有關如何配置和使用活動的詳細資訊，請參閱[此頁](../../workflow/using/extraction--file-.md)。
