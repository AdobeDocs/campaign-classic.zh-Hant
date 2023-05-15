---
product: campaign
title: 使用已命名的權限來設定權限
description: 了解如何使用已命名的權限來設定權限
badge: label="v7" type="Informity" tooltip="僅適用於Campaign Classicv7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 7%

---

# 使用已命名的權限來設定權限{#named-rights}



依預設，Adobe Campaign會提出一組命名權限，可讓您定義指派給運算子和運算子群組的授權。 您可以從 **[!UICONTROL Administration > Access management > Named rights]** 樹的節點。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**:運算子 **[!UICONTROL ADMINISTRATION]** right對執行個體具有完整存取權。 管理員使用者可以執行/建立/編輯/刪除任何物件，例如工作流程、傳送、指令碼等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**:您可以在工作流程和傳送中設定多個核准步驟，以確保目前狀態已由指派的運算子或群組核准。 具有 **[!UICONTROL APPROVAL ADMINISTRATION]** 權利可以設定批准步驟，也可以分配應批准這些步驟的操作員或操作員組。

* **[!UICONTROL CENTRAL]**:集中管理權（分散式行銷）。

* **[!UICONTROL DELETE FOLDER]**:刪除資料夾的權限。 通過此權限，用戶可以從瀏覽器視圖中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**:更改資料夾屬性的權限，如內部名稱、標籤、關聯影像、子資料夾順序等。

* **[!UICONTROL EXPORT]**:使用者可使用，將資料從其Adobe Campaign執行個體匯出至伺服器或本機電腦上的檔案 **[!UICONTROL EXPORT]** 工作流程活動。

* **[!UICONTROL FILES ACCESS]**:通過指令碼讀取和寫入檔案的權限，該指令碼可寫入 **[!UICONTROL JavaScript]** 在伺服器上讀取/寫入檔案的工作流活動。

* **[!UICONTROL IMPORT]**:一般資料匯入的權限。 **[!UICONTROL IMPORT]** 可讓您將資料匯入任何其他表格，而 **[!UICONTROL RECIPIENT IMPORT]** right僅允許匯入收件者表格。

* **[!UICONTROL INSERT FOLDERS]**:插入資料夾的權限。 具有 **[!UICONTROL INSERT FOLDERS]** 右鍵可以在資源管理器視圖的資料夾樹中建立新資料夾。

* **[!UICONTROL LOCAL]**:當地管理權（分佈式行銷）。

* **[!UICONTROL MERGE]**:將所選記錄合併為一個記錄的權限。 如果收件者存在為重複項目，則 **[!UICONTROL MERGE]** 右側允許用戶選擇重複項，並將它們合併到主要收件人中。

* **[!UICONTROL PREPARE DELIVERIES]**:建立、編輯和儲存傳遞的權限。 具有 **[!UICONTROL PREPARE DELIVERIES]** 右側也可以啟動傳遞分析程式。

* **[!UICONTROL PRIVACY DATA RIGHT]**:收集和刪除隱私權資料的權限。 如需關於此項目的詳細資訊，請參閱此[頁面](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**:用各種寫程式語言執行命令的權利。

* **[!UICONTROL RECIPIENT IMPORT]**:匯入收件者的權限。 具有 **[!UICONTROL RECIPIENT IMPORT]** 右側可將本機檔案匯入收件者表格。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 直接在資料庫上執行任何SQL命令的權限。

* **[!UICONTROL START DELIVERIES]**:核准先前分析的傳送的權限。 傳送分析後，傳送會在各種核准步驟暫停，且需要獲得核准才能繼續。 具有 **[!UICONTROL START DELIVERIES]** 允許核准傳遞的權限。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**:使用SQL資料管理活動編寫您自己的SQL指令碼，以便建立和填充工作表(請參閱 [本節](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**:直接執行工作流程。 若沒有此權限，使用者將無法啟動、停止或重新啟動工作流程。

* **[!UICONTROL WEBAPP]**:使用Web應用程式的權限。

>[!NOTE]
>
>此清單會因平台上安裝的附加元件而異。

## 訪問權限矩陣 {#access-rights-matrix}

預設組和命名權限允許操作員訪問導航層次結構中的某些資料夾，並授予讀取、寫入和刪除權限。

Adobe Campaign存取權限矩陣可供使用 [此處](/help/platform/using/assets/access-rights-matrix.pdf).

[![影像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
