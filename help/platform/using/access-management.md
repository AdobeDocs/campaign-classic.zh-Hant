---
solution: Campaign Classic
product: campaign
title: 存取管理
description: 存取管理
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: d1130691e40c0cac183db37a4c0b410d00bb696a
workflow-type: tm+mt
source-wordcount: '2984'
ht-degree: 2%

---


# 存取管理{#access-management}

## 關於權限{#about-permissions}

Adobe Campaign可讓您定義並管理指派給各種運算子的權限。 這些是授權或拒絕的一組權利和限制：

* 存取特定功能（透過指名的權利）,
* 存取特定記錄，
* 建立、修改和／或刪除記錄（活動、聯繫人、促銷活動、組等）。

權限會套用至運算元設定檔或運算元群組。

這些動作會由連結至營運商與Adobe Campaign連線模式的安全參數來完成。 有關詳細資訊，請參見[此頁面](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

您可以授予使用者兩種權限類型：

* 您可以定義屬性權限的運算子群組，然後將運算子與一或多個群組關聯。 這可讓您重複使用權限，並讓營運商設定檔更加一致。 此外，還有助於個人檔案的管理與維護。 組建立和管理在[運算子組](#operator-groups)中顯示。
* 您可以直接將指名的權限歸屬給使用者，在某些情況下，會超出透過群組分配的權限。 這些權利顯示在[命名權利](#named-rights)中。

>[!NOTE]
>
>在開始定義權限之前，Adobe建議您先閱讀[安全性設定檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。

## 運算子 {#operators}

### 關於運算子{#about-operators}

運算子是具有登入及執行動作權限的Adobe Campaign使用者。

預設情況下，運算子儲存在&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;節點中。

![](assets/s_ncs_user_list_operators.png)

可以手動建立運算子，也可以在現有LDAP目錄上映射運算子。

有關建立運算子的完整過程，請參閱[本頁](#creating-an-operator)。

如需Adobe Campaign與LDAP整合的詳細資訊，請參閱[本頁](../../installation/using/connecting-through-ldap.md)。

>[!IMPORTANT]
>
>操作員必須連結至安全區才能登入例項。 有關Adobe Campaign中安全區的詳細資訊，請參閱[本頁](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

使用者也可以使用其Adobe ID直接連線至Adobe Campaign。 如需關於此項目的詳細資訊，請參閱此[頁面](../../integrations/using/about-adobe-id.md)。

### 建立運算子{#creating-an-operator}

若要建立新的運算元並授與權限，請遵循下列步驟：

1. 按一下運算子清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，然後輸入新運算子的詳細資訊。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定使用者的&#x200B;**[!UICONTROL Identification parameters]**:其登錄名、密碼和名稱。 運算子將使用登入和密碼來登入Adobe Campaign。 用戶登錄後，他們可以通過&#x200B;**[!UICONTROL Tools > Change password]**&#x200B;菜單更改其密碼。 營運商的電子郵件至關重要，因為它可讓營運商接收通知，例如在處理核準時。

   此部分也可讓您將運算子連結至組織實體。 有關詳細資訊，請參閱[此頁](../../campaign/using/about-distributed-marketing.md)。

1. 在&#x200B;**[!UICONTROL Operator access rights]**&#x200B;區段中選擇授予操作員的權限。

   若要指派運算元的權限，請按一下權限清單上方的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後從可用群組清單中選取一組運算元：

   ![](assets/s_ncs_user_permissions_operators.png)

   您也可以選取一或多個命名權限（請參閱[命名權限](#named-rights)）。 若要這麼做，請按一下&#x200B;**[!UICONTROL Folder]**&#x200B;欄位右側的箭頭，然後選取&#x200B;**[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   選擇要分配的組和／或命名權限，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行驗證。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以建立運算子：此描述檔會新增至現有運算子的清單。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>您可以建立新的運算元資料夾，以根據您的需求來組織運算元。 若要這麼做，請在運算子資料夾上按一下滑鼠右鍵，然後選取&#x200B;**[!UICONTROL Add an 'Operators' folder]**。

在建立運算子的描述檔後，您就可以新增或更新其資訊。 要執行此操作，請按一下&#x200B;**[!UICONTROL Edit]**&#x200B;頁籤。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>**[!UICONTROL Session timeout]**&#x200B;欄位可讓您調整FDA作業逾時前的延遲。 有關詳細資訊，請參閱[關於同盟資料存取](../../installation/using/about-fda.md)。

### 運算子{#time-zone-of-the-operator}的時區

在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，可以選擇運算子的時區。 依預設，運算子在伺服器時區中運作。 不過，您也可以使用下拉式清單選取另一個時區。

本頁[說明時區配置。](../../installation/using/time-zone-management.md)

>[!NOTE]
>
>不同時區內的協作需要以UTC儲存日期。 日期會在下列上下文中在適當的時區內轉換：在用戶時區中顯示日期時，在導入和導出檔案時，在排程電子郵件傳送時，在工作流中排程活動時（調度程式、等待、時間約束等）
>
>連結至這些上下文的限制和建議會顯示在Adobe Campaign檔案的相關章節中。

此外，**[!UICONTROL Regional settings]**&#x200B;下拉式清單可讓您選擇顯示日期和數字的格式。

### 訪問權限選項{#access-rights-options}

使用&#x200B;**[!UICONTROL Access rights]**&#x200B;標籤來更新連結至運算子的群組和命名權限。

![](assets/operator_profile_security_options.png)

**[!UICONTROL Edit the access parameters...]**&#x200B;連結可讓您存取下列選項：

* **[!UICONTROL Disable account]**&#x200B;選項可讓您停用運算子的帳戶：他將無法再存取Adobe Campaign。
* **[!UICONTROL Forbid access from the rich client]**&#x200B;選項可讓您將Adobe Campaign的使用限制為[Web存取](../../platform/using/adobe-campaign-workspace.md#console-and-web-access)或透過API:無法再存取Adobe Campaign用戶端主控台。
* 可以把安全區和操作員連接起來。 有關詳細資訊，請參見[此頁面](../../installation/using/configuring-campaign-server.md#defining-security-zones)。
* 您也可以使用適當的連結來定義受信任的IP遮罩。

   如果營運商的IP位址在此清單中，則不需輸入密碼即可連線至Adobe Campaign。

   您也可以指定一組IP位址，這些位址將被授權在不使用密碼的情況下進行連線，例如在下列範例中：

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >為保全您平台的存取權，必須小心使用此選項。

* **[!UICONTROL Restrict to information found in sub-folders of:]**&#x200B;選項可讓您限制屬於資料夾運算子的權限。 用戶只能看到此選項中指定的節點的子資料夾：

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >這是非常嚴格的限制，必須謹慎使用。 以此類權限登錄的操作員只能查看指定資料夾的內容，並且無法通過瀏覽器訪問樹的任何其他節點。 不過，視他可存取的功能而定(例如：工作流程)，則他可顯示通常儲存在他看不到的節點中的資料。

### 運算子{#folders--approval-and-tasks-of-an-operator}的資料夾、核准和工作

**[!UICONTROL Audit]**&#x200B;標籤可讓您檢視與運算子相關的資訊。 根據操作員干預區中定義的設定，將各種頁籤自動添加到。

您可以存取：

* 連結至運算子之資料夾的權限清單。

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >有關詳細資訊，請參閱[資料夾訪問管理](#folder-access-management)。

* 操作員批准日誌。

   ![](assets/operator_profile_validations.png)

* 他們所訂閱的論壇清單。
* 日曆中的事件。
* 指派給它們的任務清單。

### 預設運算子{#default-operators}

Adobe Campaign使用技術營運商，預設設定了描述檔：管理員（「管理員」）、帳單（「帳單」）、監控、Web應用程式代理(「webapp」)等。 其中一些取決於平台上安裝的應用程式和選項：例如，&#39;central&#39;和&#39;local&#39;運算子只有在安裝了Distributed Marketing選項時才會顯示。

>[!IMPORTANT]
>
>當平台傳回資訊訊息時，這些技術營運商會依預設收到通知。 我們強烈建議為他們提供聯絡人電子郵件。
>
>為確保Web應用程式正常運作，我們也建議不要為「webapp」運算子定義特定的地區設定。

依預設，「webapp」技術營運商具有命名的「管理」權限，這可能導致安全風險。 若要修正此問題，建議移除此權限。 操作步驟：

1. 在&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;節點中，按一下&#x200B;**[!UICONTROL New]**&#x200B;以建立一個右側名稱，並將其命名為WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   [Named rights](#named-rights)一節中詳述了命名權限。

1. 從&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;節點中，選擇Web應用程式代理運算子(&#39;webapp&#39;)。

   選擇&#x200B;**[!UICONTROL Edit]**&#x200B;頁籤，然後選擇&#x200B;**[!UICONTROL Access rights]**&#x200B;頁籤，並從清單中刪除名為右的ADMINISTRATION。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取您剛建立的WEBAPP，然後儲存變更。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 為關注此運算子的資料夾（主要是「收件者」資料夾）指派「webapp」運算子的讀取和寫入資料存取權限。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   在[資料夾訪問管理](#folder-access-management)部分中詳細介紹了修改樹資料夾的權限。

>[!NOTE]
>
>如需安全性方針的詳細資訊，請參閱[Adobe Campaign安全性設定檢查清單](https://helpx.adobe.com/campaign/kb/acc-security.html)。

## 運算子群組{#operator-groups}

操作員組是通過樹中的&#x200B;**[!UICONTROL Administration > Access management > Operator groups]**&#x200B;節點建立的。

### 建立新運算子組{#creating-a-new-operator-group}

若要建立新的運算元群組，請套用下列步驟：

1. 按一下組清單右側的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，或按一下右鍵清單並選擇&#x200B;**[!UICONTROL New]**。
1. 在下方窗口的&#x200B;**[!UICONTROL General]**&#x200B;頁籤中，在相應欄位中輸入此組的名稱和說明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 按一下&#x200B;**[!UICONTROL Content]**&#x200B;頁籤以定義此組的授權。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選擇指定的右側或要與組關聯的運算子。
1. 按一下下拉清單或&#x200B;**[!UICONTROL Folder]**&#x200B;欄位右側的資料夾，以找到要與此組關聯的指定權限或運算子。
1. 選擇要添加的權限或運算子，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;以驗證。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重複此操作以添加其他權限或運算子。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕，將群組新增至清單。

### 預設群組{#default-groups}

預設運算元群組為：

1. **[!UICONTROL Administrator]**

   此群組中的運算子擁有執行個體的完整存取權。 管理員是可存取介面中最具技術性部分的使用者。 他們負責&#x200B;**[!UICONTROL Administration]**&#x200B;角色，並確保平台已全部設定。

   此群組包含下列指名的權限：

   * **[!UICONTROL ADMINISTRATION]**:執行／建立／編輯／刪除任何物件（例如工作流程、傳送、指令碼等）的權利。

1. **[!UICONTROL Delivery operators]**

   此群組的運算子負責管理傳送：它們可存取建立和準備傳送所需的主要資源（促銷活動類型、傳送對應、預設範本、個人化區塊等）。

   此群組包含下列命名權限：

   * **[!UICONTROL PREPARE DELIVERIES]**:直接建立、編輯和開始傳送分析，
   * **[!UICONTROL START DELIVERIES]**:核准先前分析的傳送。

1. **[!UICONTROL Campaign managers]**

   此群組中的運算子可以管理行銷促銷活動：它可讓您存取連結至促銷活動的物件（計畫、方案、工作流程、預算等） 在&#x200B;**[!UICONTROL Campaign]**&#x200B;的架構中（選用的Adobe Campaign模組）。

   此群組包含下列命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹狀結構的權利（前提是您對相關分支具有編輯權限）,
   * **[!UICONTROL WORKFLOW]**:使用工作流程。

   >[!NOTE]
   >
   >此群組不會讓運算子開始傳送。

1. **[!UICONTROL Content contributors]**

   此群組中的運算子可存取&#x200B;**[!UICONTROL Content management]**（選用的Adobe Campaign模組）架構內的「內容」資料夾。 此群組不授予任何額外權利。

1. **[!UICONTROL Access to reports]**

   此群組會保留給外部運算子，以透過Web存取存取來存取傳送報表。

1. **[!UICONTROL Workflow execution]**

   此群組可讓您指派營運商管理與促銷活動無關之工作流程的權利。

1. **[!UICONTROL Workflow supervisors]**

   此群組中的運算子會收到電子郵件通知，以防發生促銷活動工作流程的警報。

1. 本地／中央管理

   這些群組可讓您使用&#x200B;**[!UICONTROL Distributed marketing]**（選用的Adobe Campaign模組）。

1. **[!UICONTROL Offer managers]**

   此群組中的運算子可建立及維護選件。 有關此問題的詳細資訊，請參閱此[頁](../../interaction/using/operator-profiles.md)。
此群組包含下列命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹狀結構的權利（前提是您對相關分支具有編輯權限）,
   * **[!UICONTROL EDIT FOLDERS]**:有權更改資料夾屬性，如內部名稱、標籤、關聯的影像、子資料夾順序等。

## 命名權限{#named-rights}

依預設，Adobe Campaign會提出一組命名權限，可讓您定義指派給運算元和運算元群組的授權。 這些權限可從樹的&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;節點進行編輯。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**:擁有權限 **[!UICONTROL ADMINISTRATION]** 的運算子可完整存取執行個體。管理員使用者可以執行／建立／編輯／刪除任何物件，例如工作流程、傳送、指令碼等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**:您可以在工作流程和傳送中設定多個核准步驟，以確保目前狀態已由指派的營運商或群組核准。擁有&#x200B;**[!UICONTROL APPROVAL ADMINISTRATION]**&#x200B;權限的使用者可以設定核准步驟，也可以指派應核准這些步驟的運算元或運算元群組。

* **[!UICONTROL CENTRAL]**:適用於中央管理（分佈式行銷）的權利。

* **[!UICONTROL DELETE FOLDER]**:刪除資料夾的權限。通過此權限，用戶可以從瀏覽器視圖中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**:有權更改資料夾屬性，如內部名稱、標籤、關聯的影像、子資料夾順序等。

* **[!UICONTROL EXPORT]**:使用者可使用工作流程活動，將資料從其Adobe Campaign例項匯出至伺服器或本機電腦 **[!UICONTROL EXPORT]** 上的檔案。

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

Adobe Campaign存取權限表位於[這裡](/help/platform/using/assets/access-rights-matrix.pdf)。

[![影像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)

## 資料夾存取管理{#folder-access-management}

樹的每個資料夾都有附加的讀取、寫入和刪除訪問權限。 若要存取檔案，運算元或運算元群組至少必須具有讀取存取權。

### 編輯資料夾{#edit-permissions-on-a-folder}的權限

要編輯對樹的特定資料夾的權限，請執行以下步驟：

1. 按一下右鍵資料夾並選擇&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_folder_properties.png)

1. 按一下&#x200B;**[!UICONTROL Security]**&#x200B;頁籤查看此資料夾的授權。

   ![](assets/s_ncs_user_folder_properties_security.png)

### 修改權限{#modify-permissions}

若要修改權限，您可以：

* **取代群組或運算子**。若要這麼做，請按一下其中一個具有資料夾權限的群組（或運算子），然後從下拉式清單中選取新群組（或新運算子）:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **授權群組或營運商**。要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後選擇要為此資料夾分配授權的組或運算子。
* **禁止群組或營運商**。若要這麼做，請按一下&#x200B;**[!UICONTROL Delete]**&#x200B;並選取您要移除此資料夾授權的群組或運算子。
* **選擇指派給群組或運算子的權限**。若要這麼做，請按一下相關的群組或運算子，然後選取您要授與的存取權，並取消選取其他的存取權。

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 傳播權限{#propagate-permissions}

您可以傳播授權和訪問權限。 要執行此操作，請在資料夾屬性中選擇&#x200B;**[!UICONTROL Propagate]**&#x200B;選項。

然後，在此窗口中定義的授權將應用於當前節點的所有子資料夾。 然後，您可以對每個子資料夾超載這些授權。

>[!NOTE]
>
>清除資料夾的此選項不會自動清除子資料夾的選項。 您必須明確清除每個子資料夾。

### 授予對所有運算子{#grant-access-to-all-operators}的訪問權限

在&#x200B;**[!UICONTROL Security]**&#x200B;標籤中，如果選取&#x200B;**[!UICONTROL System folder]**&#x200B;選項，所有運算子都可存取此資料，不論其權限為何。 如果清除此選項，您必須將運算子（或其群組）明確新增至授權清單，以便其擁有存取權。

![](assets/s_ncs_user_folder_properties_security03b.png)

## 資料夾和視圖{#folders-and-views}

### 關於資料夾{#about-folders}

資料夾是Adobe Campaign樹狀結構中的節點。 通過按一下右鍵樹，通過&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜單建立這些節點。 依預設，第一個功能表可讓您新增與目前內容對應的資料夾。

![](assets/s_ncs_user_add_folder_in_tree.png)

您可以授予這些資料夾的權限，就像對樹的所有其他資料夾一樣。 請參閱[資料夾存取管理](#folder-access-management)。

### 關於視圖{#about-views}

此外，您還可以建立檢視，以限制資料存取，並組織樹狀結構的內容以符合您的需求。 然後，您可以指派檢視的權限。

視圖是一個資料夾，它顯示物理儲存在一個或多個相同類型的其他資料夾中的記錄。 例如，如果您建立的「促銷活動」資料夾是檢視，則預設會顯示資料庫中顯示的所有促銷活動，無論其來源為何。 然後可以篩選此資料。

將資料夾轉換為視圖時，與資料庫中存在的資料夾類型相對應的所有資料都會顯示在視圖中，而與保存資料夾無關。 然後，您可以篩選它，以限制顯示的資料清單。

>[!IMPORTANT]
>
>這些視圖包含資料並提供對其的訪問，但資料不實際儲存在視圖資料夾中。 運算子必須擁有資料來源資料夾中所需動作的適當權限（至少是讀取存取）。
>
>要在不授予對其源資料夾訪問權限的情況下授予對視圖的訪問權限，只要不授予對源資料夾父節點的讀訪問權限即可。

要區分視圖和資料夾，每個視圖的名稱以不同的顏色（深青色）顯示。

![](assets/s_ncs_user_view_name_color.png)

### 添加資料夾並建立視圖{#adding-folders-and-creating-views}

在以下範例中，我們將建立新資料夾以顯示特定資料：

1. 建立新的&#x200B;**[!UICONTROL Deliveries]**&#x200B;類型資料夾，並將它命名為&#x200B;**Deliveries France**。
1. 按一下右鍵此資料夾並選擇&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_add_folder_exple.png)

1. 在 **[!UICONTROL Restriction]** 索引標籤中，選取 **[!UICONTROL This folder is a view]**。然後會顯示資料庫中的所有傳送。

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 從視窗中間區段的查詢編輯器定義傳送篩選條件：接著會顯示與已定義篩選器對應的促銷活動。

   >[!NOTE]
   >
   >查詢編輯器顯示在[此部分](../../platform/using/about-queries-in-campaign.md)中。

   使用下列篩選條件：

![](assets/s_ncs_user_add_folder_exple00.png)

檢視中將顯示下列傳送：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>在管理[事務性消息傳遞](../../message-center/using/about-transactional-messaging.md)事件時，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;資料夾不能設定為執行實例的視圖，因為這可能導致訪問權限問題。 如需事件收集的詳細資訊，請參閱[本節](../../message-center/using/event-collection.md)。