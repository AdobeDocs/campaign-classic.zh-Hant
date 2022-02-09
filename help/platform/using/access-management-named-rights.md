---
product: campaign
title: 使用已命名的權限來設定權限
description: 瞭解如何使用命名權限設定權限
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 7%

---

# 使用已命名的權限來設定權限{#named-rights}

![](../../assets/common.svg)

預設情況下，Adobe Campaign會提出一組命名權限，用於定義分配給運算子和運算子組的授權。 可從 **[!UICONTROL Administration > Access management > Named rights]** 的子目標。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**:具有 **[!UICONTROL ADMINISTRATION]** right對實例具有完全訪問權限。 管理員用戶可以執行/建立/編輯/刪除任何對象，如工作流、交付、指令碼等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**:您可以在工作流和交貨中設定多個審批步驟，以確保當前狀態已經由分配的操作員或組審批。 具有 **[!UICONTROL APPROVAL ADMINISTRATION]** right可以設定批准步驟，還可以分配應批准這些步驟的操作員或操作員組。

* **[!UICONTROL CENTRAL]**:中央管理權限（分佈式營銷）。

* **[!UICONTROL DELETE FOLDER]**:刪除資料夾的權限。 通過此權限，用戶可以從瀏覽器視圖中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**:更改資料夾屬性（如內部名稱、標籤、關聯影像、子資料夾順序等）的權限。

* **[!UICONTROL EXPORT]**:用戶可以使用以下命令將資料從其Adobe Campaign實例導出到伺服器或本地電腦上的檔案 **[!UICONTROL EXPORT]** 工作流活動。

* **[!UICONTROL FILES ACCESS]**:通過指令碼對檔案進行讀寫訪問的權限，該指令碼可以寫入 **[!UICONTROL JavaScript]** 用於讀取/寫入伺服器上的檔案的工作流活動。

* **[!UICONTROL IMPORT]**:用於通用資料導入的權限。 **[!UICONTROL IMPORT]** 允許將資料導入任何其它表，而 **[!UICONTROL RECIPIENT IMPORT]** 僅允許導入到收件人表。

* **[!UICONTROL INSERT FOLDERS]**:插入資料夾的權限。 具有 **[!UICONTROL INSERT FOLDERS]** 在「資源管理器」視圖的資料夾樹中，「權限」可以建立新資料夾。

* **[!UICONTROL LOCAL]**:本地管理權（分佈式營銷）。

* **[!UICONTROL MERGE]**:將選定記錄合併到一個記錄中的權限。 如果收件人作為重複項存在， **[!UICONTROL MERGE]** 右側允許用戶選擇重複項並將它們合併到主收件人中。

* **[!UICONTROL PREPARE DELIVERIES]**:建立、編輯和保存交貨的權限。 具有 **[!UICONTROL PREPARE DELIVERIES]** right也可以啟動交貨分析流程。

* **[!UICONTROL PRIVACY DATA RIGHT]**:收集和刪除隱私資料的權利。 如需關於此項目的詳細資訊，請參閱此[頁面](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**:以各種寫程式語言執行命令的權利。

* **[!UICONTROL RECIPIENT IMPORT]**:導入收件人的權限。 具有 **[!UICONTROL RECIPIENT IMPORT]** 權限可以將本地檔案導入收件人表中。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 有權直接在資料庫上執行任何SQL命令。

* **[!UICONTROL START DELIVERIES]**:批准先前分析的交貨的權利。 在交付分析後，交付將在各個審批步驟中暫停，並需要獲得批准才能恢復。 具有 **[!UICONTROL START DELIVERIES]** 允許批准交貨。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**:使用SQL資料管理活動編寫自己的SQL指令碼以建立和填充工作表的權利(請參見 [此部分](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**:執行工作流的權限。 沒有此權限，用戶將無法啟動、停止或重新啟動工作流。

* **[!UICONTROL WEBAPP]**:有權使用Web應用程式。

>[!NOTE]
>
>此清單可能因平台上安裝的載入項而異。

## 訪問權限矩陣 {#access-rights-matrix}

預設組和命名權限允許操作員訪問導航層次結構中的某些資料夾，並授予讀、寫和刪除權限。

Adobe Campaign訪問權限清單可用 [這裡](/help/platform/using/assets/access-rights-matrix.pdf)。

[![影像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
