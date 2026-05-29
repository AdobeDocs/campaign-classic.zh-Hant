---
product: campaign
title: 使用已命名的權限來設定權限
description: 瞭解如何使用已命名的許可權來設定許可權
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
TQID: https://experienceleague.adobe.com/GApH-ZtovMX--PzISD-Pvafo3pfcbG-OqHzp5kCvcNQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 652
ht-degree: 4%

---

# 使用已命名的權限來設定權限{#named-rights}

依預設，Adobe Campaign會建議一組已命名的許可權，讓您定義指派給運運算元和運運算元群組的授權。 可以從樹狀結構的&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;節點編輯這些許可權。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**：具有&#x200B;**[!UICONTROL ADMINISTRATION]**&#x200B;許可權的運運算元具有執行個體的完整存取權。 管理員使用者可以執行/建立/編輯/刪除任何物件，例如工作流程、傳送、指令碼等。

  >[!IMPORTANT]
  >
  >**移轉至IMS後：**&#x200B;移轉至Adobe Identity Management系統(IMS)後，任何名稱中包含「管理員」字樣的產品設定檔或命名許可權（例如「管理員」、「管理員」、「管理員」等） 會自動授與「Campaign控制面板」的存取權。 建議您避免在已命名的許可權或角色名稱中使用「管理員」，除非您想讓這些使用者擁有控制面板存取權。 深入瞭解[IMS移轉](../../technotes/using/migrate-users-to-ims.md)和[管理控制面板存取](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}。

* **[!UICONTROL APPROVAL ADMINISTRATION]**：您可以在工作流程與傳遞中設定多個核准步驟，以確保指派的運運算元或群組已核准目前狀態。 具有&#x200B;**[!UICONTROL APPROVAL ADMINISTRATION]**&#x200B;許可權的使用者可以設定核准步驟，也可以指派應核准這些步驟的運運算元或運運算元群組。

  >[!IMPORTANT]
  >
  >**移轉至IMS後：**&#x200B;產品設定檔或包含「管理員」字樣的已命名許可權（例如「核准管理員」）將授予對Campaign控制面板的存取權。 深入瞭解[IMS移轉](../../technotes/using/migrate-users-to-ims.md)和[管理控制面板存取](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}。

* **[!UICONTROL CENTRAL]**：適用於集中管理（分散式行銷）。

* **[!UICONTROL DELETE FOLDER]**：刪除資料夾的許可權。 透過此許可權，使用者可以從檔案總管檢視中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**：變更資料夾屬性的權利，例如內部名稱、標籤、關聯的影像、子資料夾順序等。

* **[!UICONTROL EXPORT]**：使用者可以使用&#x200B;**[!UICONTROL EXPORT]**&#x200B;工作流程活動，將資料從其Adobe Campaign執行個體匯出至伺服器或本機電腦上的檔案。

* **[!UICONTROL FILES ACCESS]**：透過指令碼讀取和寫入檔案的許可權，指令碼可在&#x200B;**[!UICONTROL JavaScript]**&#x200B;工作流程活動中寫入，以讀取/寫入伺服器上的檔案。

* **[!UICONTROL IMPORT]**：一般資料匯入的許可權。 **[!UICONTROL IMPORT]**&#x200B;可讓您將資料匯入任何其他資料表，而&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;許可權僅允許匯入收件者資料表。

* **[!UICONTROL INSERT FOLDERS]**：插入資料夾的許可權。 具有&#x200B;**[!UICONTROL INSERT FOLDERS]**&#x200B;許可權的使用者可以在檔案總管檢視的資料夾樹狀結構中建立新資料夾。

* **[!UICONTROL LOCAL]**：直接用於本機管理（分散式行銷）。

* **[!UICONTROL MERGE]**：直接將選取的記錄合併為一個。 如果收件者以重複專案存在，**[!UICONTROL MERGE]**&#x200B;許可權可讓使用者選取重複專案，並將其合併至主要收件者。

* **[!UICONTROL PREPARE DELIVERIES]**：建立、編輯和儲存傳遞的權利。 具有&#x200B;**[!UICONTROL PREPARE DELIVERIES]**&#x200B;許可權的使用者也可以開始傳遞分析程式。

* **[!UICONTROL PRIVACY DATA RIGHT]**：收集和刪除隱私資料的權利。 如需關於此項目的詳細資訊，請參閱此[頁面](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**：以各種程式語言執行命令的權利。

* **[!UICONTROL RECIPIENT IMPORT]**：匯入收件者的權利。 具有&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;許可權的使用者可以將本機檔案匯入收件者表格。

* **[!UICONTROL SQL SCRIPT EXECUTION]**&#x200B;直接在資料庫上執行任何SQL命令的許可權。

* **[!UICONTROL START DELIVERIES]**：核准先前分析的傳遞的許可權。 傳遞分析後，傳遞會在各種核准步驟暫停，並需要核准才能繼續。 具有&#x200B;**[!UICONTROL START DELIVERIES]**&#x200B;許可權的使用者可核准傳遞。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**：使用SQL資料管理活動撰寫您自己的SQL指令碼，以建立和填入工作表格。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-data-management.html?lang=zh-Hant){target="_blank"}。

* **[!UICONTROL WORKFLOW]**：執行工作流程的許可權。 若無此許可權，使用者就無法啟動、停止或重新啟動工作流程。

* **[!UICONTROL WEBAPP]**：使用Web應用程式的許可權。

>[!NOTE]
>
>此清單可能會因平台上安裝的附加元件而異。

## 存取許可權矩陣 {#access-rights-matrix}

預設群組和已命名的許可權可讓操作者存取導覽階層中的特定資料夾，並授予讀取、寫入和刪除許可權。

[此處](/help/platform/using/assets/access-rights-matrix.pdf)提供Adobe Campaign存取權矩陣。

[![影像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=zh-Hant)
