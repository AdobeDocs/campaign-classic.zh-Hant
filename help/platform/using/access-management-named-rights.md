---
product: campaign
title: 使用已命名的權限來設定權限
description: 瞭解如何使用已命名的許可權來設定許可權
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 6%

---

# 使用已命名的權限來設定權限{#named-rights}



依預設，Adobe Campaign會建議一組已命名的許可權，讓您定義指派給運運算元和運運算元群組的授權。 這些許可權可從以下位置編輯： **[!UICONTROL Administration > Access management > Named rights]** 樹狀結構的節點。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**：運運算元與 **[!UICONTROL ADMINISTRATION]** 許可權具有執行個體的完整存取權。 管理員使用者可以執行/建立/編輯/刪除任何物件，例如工作流程、傳送、指令碼等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**：您可以在工作流程與傳送中設定多個核准步驟，以確保指派的運運算元或群組已核准目前狀態。 使用者具有 **[!UICONTROL APPROVAL ADMINISTRATION]** 許可權可以設定核准步驟，也可以指派應核准這些步驟的運運算元或運運算元群組。

* **[!UICONTROL CENTRAL]**：適用於集中管理（分散式行銷）。

* **[!UICONTROL DELETE FOLDER]**：刪除資料夾的許可權。 透過此許可權，使用者可以從檔案總管檢視中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**：變更資料夾屬性的權利，例如內部名稱、標籤、關聯的影像、子資料夾順序等。

* **[!UICONTROL EXPORT]**：使用者可使用將資料從其Adobe Campaign執行個體匯出至伺服器或本機電腦上的檔案 **[!UICONTROL EXPORT]** 工作流程活動。

* **[!UICONTROL FILES ACCESS]**：透過指令碼對檔案的讀寫存取權，該指令碼可在 **[!UICONTROL JavaScript]** 讀取/寫入伺服器檔案的工作流程活動。

* **[!UICONTROL IMPORT]**：適用於一般資料匯入。 **[!UICONTROL IMPORT]** 可讓您將資料匯入任何其他表格，而 **[!UICONTROL RECIPIENT IMPORT]** 許可權僅允許匯入收件者表格。

* **[!UICONTROL INSERT FOLDERS]**：插入資料夾的許可權。 使用者具有 **[!UICONTROL INSERT FOLDERS]** 您可以在「總管」檢視的資料夾樹狀結構中建立新資料夾。

* **[!UICONTROL LOCAL]**：本機管理許可權（分散式行銷）。

* **[!UICONTROL MERGE]**：直接將選取的記錄合併成記錄。 如果收件者以重複專案存在， **[!UICONTROL MERGE]** 許可權可讓使用者選取重複專案，並將其合併至主要收件者。

* **[!UICONTROL PREPARE DELIVERIES]**：建立、編輯和儲存傳送的權利。 使用者具有 **[!UICONTROL PREPARE DELIVERIES]** 右側也可以開始傳遞分析程式。

* **[!UICONTROL PRIVACY DATA RIGHT]**：收集和刪除隱私資料的權利。 如需關於此項目的詳細資訊，請參閱此[頁面](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**：以各種程式語言執行命令的權利。

* **[!UICONTROL RECIPIENT IMPORT]**：匯入收件者的權利。 使用者具有 **[!UICONTROL RECIPIENT IMPORT]** 許可權可以將本機檔案匯入收件者表格。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 直接在資料庫上執行任何SQL命令的許可權。

* **[!UICONTROL START DELIVERIES]**：核准先前分析的傳送的許可權。 傳遞分析後，傳遞會在各種核准步驟暫停，並需要核准才能繼續。 使用者具有 **[!UICONTROL START DELIVERIES]** 許可權可用於核准傳遞。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**：有權使用SQL資料管理活動編寫您自己的SQL指令碼，以建立和填入工作表(請參閱 [本節](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**：執行工作流程的許可權。 若無此許可權，使用者就無法啟動、停止或重新啟動工作流程。

* **[!UICONTROL WEBAPP]**：使用網頁應用程式的許可權。

>[!NOTE]
>
>此清單可能會因平台上安裝的附加元件而異。

## 存取許可權矩陣 {#access-rights-matrix}

預設群組和已命名的許可權可讓操作者存取導覽階層中的特定資料夾，並授予讀取、寫入和刪除許可權。

現提供Adobe Campaign存取許可權矩陣 [此處](/help/platform/using/assets/access-rights-matrix.pdf).

[![影像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf)
