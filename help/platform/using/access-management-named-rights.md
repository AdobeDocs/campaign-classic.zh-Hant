---
product: campaign
title: 使用已命名的權限來設定權限
description: 了解如何使用已命名的權限來設定權限
feature: 存取管理
role: Business Practitioner, Administrator
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 7%

---

# 使用已命名的權限來設定權限{#named-rights}

依預設，Adobe Campaign會提出一組命名權限，可讓您定義指派給運算子和運算子群組的授權。 可以從樹的&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;節點編輯這些權限。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**:具有權限 **[!UICONTROL ADMINISTRATION]** 的運算子可完整存取執行個體。管理員使用者可以執行/建立/編輯/刪除任何物件，例如工作流程、傳送、指令碼等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**:您可以在工作流程和傳送中設定多個核准步驟，以確保目前狀態已由指派的運算子或群組核准。具有&#x200B;**[!UICONTROL APPROVAL ADMINISTRATION]**&#x200B;權限的使用者可以設定核准步驟，也可指派應核准這些步驟的運算子或運算子群組。

* **[!UICONTROL CENTRAL]**:集中管理權（分散式行銷）。

* **[!UICONTROL DELETE FOLDER]**:刪除資料夾的權限。通過此權限，用戶可以從瀏覽器視圖中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**:更改資料夾屬性的權限，如內部名稱、標籤、關聯影像、子資料夾順序等。

* **[!UICONTROL EXPORT]**:使用者可以使用工作流程活動，將資料從其Adobe Campaign例項匯出至伺服器或本機 **[!UICONTROL EXPORT]** 上的檔案。

* **[!UICONTROL FILES ACCESS]**:通過指令碼對檔案進行讀寫訪問，該指令碼可寫入工作流 **[!UICONTROL JavaScript]** 活動中以讀取/寫入伺服器上的檔案。

* **[!UICONTROL IMPORT]**:一般資料匯入的權限。**[!UICONTROL IMPORT]** 可讓您將資料匯入任何其他表格，而 **[!UICONTROL RECIPIENT IMPORT]** 右側僅允許匯入至收件者表格。

* **[!UICONTROL INSERT FOLDERS]**:插入資料夾的權限。右&#x200B;**[!UICONTROL INSERT FOLDERS]**&#x200B;的用戶可以在資源管理器視圖中的資料夾樹中建立新資料夾。

* **[!UICONTROL LOCAL]**:當地管理權（分佈式行銷）。

* **[!UICONTROL MERGE]**:將所選記錄合併為一個記錄的權限。如果收件者存在為重複項目，**[!UICONTROL MERGE]**&#x200B;右側可讓使用者選取重複項目，並將其合併為主要收件者。

* **[!UICONTROL PREPARE DELIVERIES]**:建立、編輯和儲存傳遞的權限。右側&#x200B;**[!UICONTROL PREPARE DELIVERIES]**&#x200B;的使用者也可以開始傳送分析程式。

* **[!UICONTROL PRIVACY DATA RIGHT]**:收集和刪除隱私權資料的權限。如需關於此項目的詳細資訊，請參閱此[頁面](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**:用各種寫程式語言執行命令的權利。

* **[!UICONTROL RECIPIENT IMPORT]**:匯入收件者的權限。具有&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;權限的使用者可將本機檔案匯入收件者表格。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 直接在資料庫上執行任何SQL命令的權限。

* **[!UICONTROL START DELIVERIES]**:核准先前分析的傳送的權限。傳送分析後，傳送會在各種核准步驟暫停，且需要獲得核准才能繼續。 具有&#x200B;**[!UICONTROL START DELIVERIES]**&#x200B;權限的使用者可以核准傳送。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**:使用SQL資料管理活動編寫您自己的SQL指令碼，以便建立和填充工作表(請參 [閱本節](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**:直接執行工作流程。若沒有此權限，使用者將無法啟動、停止或重新啟動工作流程。

* **[!UICONTROL WEBAPP]**:使用Web應用程式的權限。

>[!NOTE]
>
>此清單會因平台上安裝的附加元件而異。

## 訪問權限矩陣{#access-rights-matrix}

預設組和命名權限允許操作員訪問導航層次結構中的某些資料夾，並授予讀取、寫入和刪除權限。

Adobe Campaign存取權限矩陣可在[此處](/help/platform/using/assets/access-rights-matrix.pdf)取得。

[![影像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
