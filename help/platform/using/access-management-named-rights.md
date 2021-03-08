---
solution: Campaign Classic
product: campaign
title: 使用命名權限來設定權限
description: 瞭解如何使用命名權限來設定權限
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 4%

---


# 使用命名權限來設定權限{#named-rights}

依預設，Adobe Campaign會提出一組命名權限，讓您定義指派給運算元和運算元群組的授權。 這些權限可從樹的&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;節點進行編輯。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**:擁有權限 **[!UICONTROL ADMINISTRATION]** 的運算子可完整存取執行個體。管理員使用者可以執行／建立／編輯／刪除任何物件，例如工作流程、傳送、指令碼等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**:您可以在工作流程和傳送中設定多個核准步驟，以確保目前狀態已由指派的營運商或群組核准。擁有&#x200B;**[!UICONTROL APPROVAL ADMINISTRATION]**&#x200B;權限的使用者可以設定核准步驟，也可以指派應核准這些步驟的運算元或運算元群組。

* **[!UICONTROL CENTRAL]**:適用於中央管理（分佈式行銷）的權利。

* **[!UICONTROL DELETE FOLDER]**:刪除資料夾的權限。通過此權限，用戶可以從瀏覽器視圖中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**:有權更改資料夾屬性，如內部名稱、標籤、關聯的影像、子資料夾順序等。

* **[!UICONTROL EXPORT]**:使用者可使用工作流程活動，將資料從其Adobe Campaign例項匯出至伺服器或本機 **[!UICONTROL EXPORT]** 上的檔案。

* **[!UICONTROL FILES ACCESS]**:有權通過指令碼讀取和寫入檔案，該指令碼可寫入工作流 **[!UICONTROL JavaScript]** 活動中，以讀取／寫入伺服器上的檔案。

* **[!UICONTROL IMPORT]**:通用資料匯入的權限。**[!UICONTROL IMPORT]** 允許您將資料導入任何其它表，而 **[!UICONTROL RECIPIENT IMPORT]** 右側僅允許導入到收件者表。

* **[!UICONTROL INSERT FOLDERS]**:右鍵插入資料夾。右側&#x200B;**[!UICONTROL INSERT FOLDERS]**&#x200B;的用戶可以在資源管理器視圖中的資料夾樹中建立新資料夾。

* **[!UICONTROL LOCAL]**:適用於本地管理（分佈式行銷）的權利。

* **[!UICONTROL MERGE]**:將選定記錄合併為一個記錄的右側。如果收件者是重複的，則&#x200B;**[!UICONTROL MERGE]**&#x200B;右側允許用戶選擇複製項，並將它們合併到主要收件者中。

* **[!UICONTROL PREPARE DELIVERIES]**:直接建立、編輯和儲存傳送。右側&#x200B;**[!UICONTROL PREPARE DELIVERIES]**&#x200B;的使用者也可以開始傳送分析程式。

* **[!UICONTROL PRIVACY DATA RIGHT]**:收集和刪除隱私權資料的權利。如需關於此項目的詳細資訊，請參閱此[頁面](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**:以各種寫程式語言執行命令的權利。

* **[!UICONTROL RECIPIENT IMPORT]**:匯入收件者的權限。具有&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;權限的用戶可以將本地檔案導入收件人表。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 直接在資料庫上執行任何SQL命令的權限。

* **[!UICONTROL START DELIVERIES]**:核准先前分析之交貨的權利。在傳送分析後，傳送會在不同的核准步驟中暫停，而且需要核准才能繼續。 擁有&#x200B;**[!UICONTROL START DELIVERIES]**&#x200B;權限的使用者可以核准傳送。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**:使用SQL資料管理活動編寫自己的SQL指令碼，以便建立和填充工作表(請參 [閱本節](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**:執行工作流程的權限。沒有這項權限，使用者就無法啟動、停止或重新啟動工作流程。

* **[!UICONTROL WEBAPP]**:使用Web應用程式的權利。

>[!NOTE]
>
>此清單可能因平台上安裝的附加模組而異。

## 訪問權限矩陣{#access-rights-matrix}

預設群組和命名權限可讓運算子存取導覽階層中的特定資料夾，並授與讀取、寫入和刪除權限。

Adobe Campaign訪問權限矩陣可在[這裡](/help/platform/using/assets/access-rights-matrix.pdf)獲得。

[![影像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
