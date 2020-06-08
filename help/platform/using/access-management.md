---
title: 存取管理
seo-title: 存取管理
description: 存取管理
seo-description: null
page-status-flag: never-activated
uuid: 3f0cfa8f-1511-4445-9acb-b5be46e78295
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: c0eb06fd-192c-4ee4-9a38-c9bedbe6aea0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 651dfdab75f64d72a1c5beb1273a878ee7102b47
workflow-type: tm+mt
source-wordcount: '2912'
ht-degree: 0%

---


# 存取管理{#access-management}

## About permissions {#about-permissions}

Adobe Campaign可讓您定義並管理指派給各種運算子的權限。 這些是授權或拒絕的一組權利和限制：

* 存取特定功能（透過指名的權利）,
* 存取特定記錄，
* 建立、修改和／或刪除記錄（活動、聯繫人、促銷活動、組等）。

權限會套用至運算元設定檔或運算元群組。

這些動作會由連結至營運商與Adobe Campaign連線模式的安全參數來完成。 有關詳細資訊，請參見[此頁面](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

您可以授予使用者兩種權限類型：

* 您可以定義屬性權限的運算子群組，然後將運算子與一或多個群組關聯。 這可讓您重複使用權限，並讓營運商設定檔更加一致。 此外，還有助於個人檔案的管理與維護。 群組建立和管理會顯示在運算 [元群組中](#operator-groups)。
* 您可以直接將指名的權限歸屬給使用者，在某些情況下，會超出透過群組分配的權限。 這些權利以命名 [權利呈現](#named-rights)。

>[!NOTE]
>
>在開始定義權限之前，Adobe建議您先閱讀「安全性 [設定」檢查清單](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)。

## 運算子 {#operators}

### 關於運算子 {#about-operators}

運算子是具有登入及執行動作權限的Adobe Campaign使用者。

預設情況下，運算子儲存在節 **[!UICONTROL Administration > Access management > Operators]** 點中。

![](assets/s_ncs_user_list_operators.png)

可以手動建立運算子，也可以在現有LDAP目錄上映射運算子。

本頁說明建立運算子的完 [整程式](#creating-an-operator)。

有關Adobe Campaign和LDAP整合的詳細資訊，請參 [閱本頁](../../installation/using/connecting-through-ldap.md)。

>[!IMPORTANT]
>
>操作員必須連結至安全區才能登入例項。 如需Adobe Campaign中安全區的詳細資訊，請參 [閱本頁](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

使用者也可以使用其Adobe ID直接連線至Adobe Campaign。 For more on this, refer to this [page](../../integrations/using/about-adobe-id.md).

### 建立運算子 {#creating-an-operator}

若要建立新的運算元並授與權限，請遵循下列步驟：

1. 按一下運 **[!UICONTROL New]** 算符清單上方的按鈕，然後輸入新運算子的詳細資訊。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定使 **[!UICONTROL Identification parameters]** 用者： 其登錄名、密碼和名稱。 運算子將使用登入和密碼來登入Adobe Campaign。 使用者登入後，就可透過功能表變更其密 **[!UICONTROL Tools > Change password]** 碼。 營運商的電子郵件至關重要，因為它可讓營運商接收通知，例如在處理核準時。

   此部分也可讓您將運算子連結至組織實體。 For more on this, refer to the [this page](../../campaign/using/about-distributed-marketing.md).

1. 在區段中選取授予運算子的權 **[!UICONTROL Operator access rights]** 限。

   若要指派運算元的權限，請按一 **[!UICONTROL Add]** 下位於權限清單上方的按鈕，然後從可用群組清單中選取一組運算元：

   ![](assets/s_ncs_user_permissions_operators.png)

   您也可以選取一或多個命名權限(請參 [閱命名權限](#named-rights))。 若要這麼做，請按一下欄位右側的箭 **[!UICONTROL Folder]** 頭，然後選取 **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   選擇要分配的組和／或命名權限，然後按一下 **[!UICONTROL OK]** 驗證。

1. 按一 **[!UICONTROL Ok]** 下以建立運算子： 此描述檔會新增至現有運算子的清單。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>您可以建立新的運算元資料夾，以根據您的需求來組織運算元。 若要這麼做，請在運算子資料夾上按一下滑鼠右鍵，然後選取 **[!UICONTROL Add an 'Operators' folder]**。

在建立運算子的描述檔後，您就可以新增或更新其資訊。 若要這麼做，請按一下標 **[!UICONTROL Edit]** 簽。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>欄位 **[!UICONTROL Session timeout]** 可讓您調整FDA作業逾時前的延遲。 有關詳細資訊，請參閱關於 [同盟資料存取](../../platform/using/about-fda.md)。

### 運算子的時區 {#time-zone-of-the-operator}

在標 **[!UICONTROL General]** 簽中，可以選擇運算子的時區。 依預設，運算子在伺服器時區中運作。 不過，您也可以使用下拉式清單選取另一個時區。

本頁介紹時區 [配置](../../installation/using/time-zone-management.md)。

>[!NOTE]
>
>不同時區內的協作需要以UTC儲存日期。 日期會在下列上下文中在適當的時區內轉換： 在用戶時區中顯示日期時，在導入和導出檔案時，在排程電子郵件傳送時，在工作流中排程活動時（調度程式、等待、時間約束等）
>
>連結至這些上下文的限制和建議會顯示在Adobe Campaign檔案的相關章節中。

此外，下拉 **[!UICONTROL Regional settings]** 式清單可讓您選擇顯示日期和數字的格式。

### 存取權限選項 {#access-rights-options}

使用標 **[!UICONTROL Access rights]** 簽來更新連結至運算子的群組和命名權限。

![](assets/operator_profile_security_options.png)

The **[!UICONTROL Edit the access parameters...]** link lets you access the following options:

* 選 **[!UICONTROL Disable account]** 項可讓您停用運算子的帳戶： 他將無法再存取Adobe Campaign。
* 選 **[!UICONTROL Forbid access from the rich client]** 項可讓您將Adobe Campaign的使用限制為 [網路存取](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) ，或透過API: 無法再存取Adobe Campaign用戶端主控台。
* 可以把安全區和操作員連接起來。 有關詳細資訊，請參見[此頁面](../../installation/using/configuring-campaign-server.md#defining-security-zones)。
* 您也可以使用適當的連結來定義受信任的IP遮罩。

   如果營運商的IP位址在此清單中，則不需輸入密碼即可連線至Adobe Campaign。

   您也可以指定一組IP位址，這些位址將被授權在不使用密碼的情況下進行連線，例如在下列範例中：

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >為保全您平台的存取權，必須小心使用此選項。

* 選 **[!UICONTROL Restrict to information found in sub-folders of:]** 項可讓您限制屬於資料夾運算子的權限。 用戶只能看到此選項中指定的節點的子資料夾：

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >這是非常嚴格的限制，必須謹慎使用。 以此類權限登錄的操作員只能查看指定資料夾的內容，並且無法通過瀏覽器訪問樹的任何其他節點。 不過，視他可存取的功能而定(例如： 工作流程)，則他可顯示通常儲存在他看不到的節點中的資料。

### 操作員的資料夾、批准和任務 {#folders--approval-and-tasks-of-an-operator}

此標 **[!UICONTROL Audit]** 簽可讓您檢視與運算子相關的資訊。 根據操作員干預區中定義的設定，將各種頁籤自動添加到。

您可以存取：

* 連結至運算子之資料夾的權限清單。

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >有關詳細資訊，請參閱「文 [件夾訪問管理」](#folder-access-management)。

* 操作員批准日誌。

   ![](assets/operator_profile_validations.png)

* 他們所訂閱的論壇清單。
* 日曆中的事件。
* 指派給它們的任務清單。

### 預設運算子 {#default-operators}

Adobe Campaign使用技術營運商，預設設定了描述檔： 管理員（「管理員」）、帳單（「帳單」）、監控、Web應用程式代理(「webapp」)等。 其中一些取決於平台上安裝的應用程式和選項： 例如，&#39;central&#39;和&#39;local&#39;運算子只有在安裝了Distributed Marketing選項時才會顯示。

>[!IMPORTANT]
>
>當平台傳回資訊訊息時，這些技術營運商會依預設收到通知。 我們強烈建議為他們提供聯絡人電子郵件。
>
>為確保Web應用程式正常運作，我們也建議不要為「webapp」運算子定義特定的地區設定。

依預設，「webapp」技術營運商具有命名的「管理」權限，這可能導致安全風險。 若要修正此問題，建議移除此權限。 操作步驟：

1. 從節 **[!UICONTROL Administration > Access management > Named rights]** 點按一 **[!UICONTROL New]** 下以建立右側並命名為WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   「命名權限」一節中詳細 [介紹了命名權](#named-rights) 。

1. 從節 **[!UICONTROL Administration > Access management > Operators]** 點中，選擇Web應用程式代理運算子(&#39;webapp&#39;)。

   選擇選 **[!UICONTROL Edit]** 項卡，然後選擇 **[!UICONTROL Access rights]** 該頁籤，並從清單中刪除直接命名的ADMINISTRATION。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   按一 **[!UICONTROL Add]** 下並選取您剛建立的WEBAPP，然後儲存您所做的變更。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 為關注此運算子的資料夾（主要是「收件者」資料夾）指派「webapp」運算子的讀取和寫入資料存取權限。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   修改樹資料夾的權限在「資料夾訪問管理」 [部分中有詳細說明](#folder-access-management) 。

>[!NOTE]
>
>如需安全性方針的詳細資訊，請參閱 [Adobe Campaign安全性設定檢查清單](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)。

## 運算元群組 {#operator-groups}

操作員組是通過樹中 **[!UICONTROL Administration > Access management > Operator groups]** 的節點建立的。

### 建立新的運算元群組 {#creating-a-new-operator-group}

若要建立新的運算元群組，請套用下列步驟：

1. 按一下 **[!UICONTROL New]** 群組清單右側的按鈕，或以滑鼠右鍵按一下清單並選擇 **[!UICONTROL New]**。
1. 在下方的節窗口的頁籤 **[!UICONTROL General]** 中，在相應欄位中輸入此組的名稱和說明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 按一下 **[!UICONTROL Content]** 標籤以定義此群組的授權。
1. 按一下 **[!UICONTROL Add]** 按鈕，以選擇指定的右側或要關聯至群組的運算子。
1. 按一下欄位右側的下拉式清單或資料夾，以找 **[!UICONTROL Folder]** 出要與此群組產生關聯的指定權限或運算子。
1. 選擇要添加的權限或運算子，然後按一下 **[!UICONTROL OK]** 驗證。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重複此操作以添加其他權限或運算子。

1. 按一下 **[!UICONTROL Save]** 按鈕，將群組新增至清單。

### 預設群組 {#default-groups}

預設運算元群組為：

1. 傳送營運商

   此群組的運算子負責管理傳送： 它們可存取建立和準備傳送所需的主要資源（促銷活動類型、傳送對應、預設範本、個人化區塊等）。

   此群組包含下列命名權限：

   * 準備交貨： 直接建立、編輯和開始傳送分析，
   * 開始傳送： 核准先前分析的傳送。

1. 促銷活動管理員

   此群組中的運算子可以管理行銷促銷活動： 它可讓您存取連結至促銷活動的物件（計畫、方案、工作流程、預算等）。

   此群組包含下列命名權限：

   * 插入資料夾： 將資料夾插入Adobe Campaign樹狀結構的權利（前提是您對相關分支具有編輯權限）,
   * 工作流程： 使用工作流程。
   >[!NOTE]
   >
   >此群組不會讓運算子開始傳送。

1. 內容提供者

   此群組中的運算子可在內容管理（選用的Adobe Campaign模組）架構內 **存取「內容** 」資料夾。 此群組不授予任何額外權利。

1. 存取報表

   此群組會保留給外部運算子，以透過Web存取存取來存取傳送報表。

1. 工作流程執行

   此群組可讓您指派營運商管理與促銷活動無關之工作流程的權利。

1. 工作流程主管

   此群組中的運算子會收到電子郵件通知，以防發生促銷活動工作流程的警報。

1. 本地／中央管理

   這些群組可讓您使 **用「分散式行銷** 」（選用的Adobe Campaign模組）。

1. 選件經理

   此群組中的運算子可建立及維護選件。 For more information on this, refer to this [page](../../interaction/using/operator-profiles.md).
此群組包含下列命名權限：

   * 插入資料夾： 將資料夾插入Adobe Campaign樹狀結構的權利（前提是您對相關分支具有編輯權限）,
   * 編輯資料夾： 有權更改資料夾屬性，如內部名稱、標籤、關聯的影像、子資料夾順序等。

## 命名權限 {#named-rights}

依預設，Adobe Campaign會提出一組命名權限，可讓您定義指派給運算元和運算元群組的授權。 這些權限可從樹的節 **[!UICONTROL Administration > Access management > Named rights]** 點進行編輯。

![](assets/s_ncs_admin_named_rights.png)

這些權利如下：

* **[!UICONTROL ADMINISTRATION]**: 擁有權限 **[!UICONTROL ADMINISTRATION]** 的運算子可完整存取執行個體。 管理員使用者可以執行／建立／編輯／刪除任何物件，例如工作流程、傳送、指令碼等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**: 您可以在工作流程和傳送中設定多個核准步驟，以確保目前狀態已由指派的營運商或群組核准。 具有權限 **[!UICONTROL APPROVAL ADMINISTRATION]** 的使用者可以設定核准步驟，也可以指派應核准這些步驟的運算元或運算元群組。

* **[!UICONTROL CENTRAL]**: 適用於中央管理（分佈式行銷）的權利。

* **[!UICONTROL DELETE FOLDER]**: 刪除資料夾的權限。 通過此權限，用戶可以從瀏覽器視圖中刪除資料夾。

* **[!UICONTROL EDIT FOLDERS]**: 有權更改資料夾屬性，如內部名稱、標籤、關聯的影像、子資料夾順序等。

* **[!UICONTROL EXPORT]**: 使用者可使用工作流程活動，將資料從其Adobe Campaign例項匯出至伺服器或本機電腦 **[!UICONTROL EXPORT]** 上的檔案。

* **[!UICONTROL FILES ACCESS]**: 有權通過指令碼讀取和寫入檔案，該指令碼可以寫入工作流活 **[!UICONTROL JavaScript]** 動中，以讀取／寫入伺服器上的檔案。

* **[!UICONTROL IMPORT]**: 通用資料匯入的權限。 **[!UICONTROL IMPORT]** 允許您將資料導入任何其它表，而右 **[!UICONTROL RECIPIENT IMPORT]** 側僅允許導入到收件者表。

* **[!UICONTROL INSERT FOLDERS]**: 右鍵插入資料夾。 具有右側權 **[!UICONTROL INSERT FOLDERS]** 限的用戶可以在瀏覽器視圖中的資料夾樹中建立新資料夾。

* **[!UICONTROL LOCAL]**: 適用於本地管理（分佈式行銷）的權利。

* **[!UICONTROL MERGE]**: 將選定記錄合併為一個記錄的右側。 如果收件者是重複的，右 **[!UICONTROL MERGE]** 側會允許用戶選擇重複項並將它們合併到主要收件人中。

* **[!UICONTROL PREPARE DELIVERIES]**: 直接建立、編輯和儲存傳送。 擁有權限 **[!UICONTROL PREPARE DELIVERIES]** 的使用者也可以開始傳送分析程式。

* **[!UICONTROL PRIVACY DATA RIGHT]**: 收集和刪除隱私權資料的權利。 For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: 以各種寫程式語言執行命令的權利。

* **[!UICONTROL RECIPIENT IMPORT]**: 匯入收件者的權限。 擁有權限 **[!UICONTROL RECIPIENT IMPORT]** 的使用者可以將本機檔案匯入收件者表格。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 直接在資料庫上執行任何SQL命令的權限。

* **[!UICONTROL START DELIVERIES]**: 核准先前分析之交貨的權利。 在傳送分析後，傳送會在不同的核准步驟中暫停，而且需要核准才能繼續。 擁有權限 **[!UICONTROL START DELIVERIES]** 的使用者可以核准傳送。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: 使用SQL資料管理活動編寫自己的SQL指令碼，以便建立和填充工作表(請參 [閱本節](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**: 執行工作流程的權限。 沒有這項權限，使用者就無法啟動、停止或重新啟動工作流程。

* **[!UICONTROL WEBAPP]**: 使用Web應用程式的權利。

>[!NOTE]
>
>此清單可能因平台上安裝的附加模組而異。

## 存取權限矩陣 {#access-rights-matrix}

預設群組和命名權限可讓運算子存取導覽階層中的特定資料夾，並授與讀取、寫入和刪除權限。

Adobe Campaign存取權限表可從這裡取 [得](/help/platform/using/assets/accessrights.pdf)。

## 資料夾存取管理 {#folder-access-management}

樹的每個資料夾都有附加的讀取、寫入和刪除訪問權限。 若要存取檔案，運算元或運算元群組至少必須具有讀取存取權。

### 編輯資料夾的權限 {#edit-permissions-on-a-folder}

要編輯對樹的特定資料夾的權限，請執行以下步驟：

1. 按一下右鍵資料夾並選擇 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_folder_properties.png)

1. 按一下該 **[!UICONTROL Security]** 頁籤可查看此資料夾的授權。

   ![](assets/s_ncs_user_folder_properties_security.png)

### 修改權限 {#modify-permissions}

若要修改權限，您可以：

* **取代群組或運算子**。 若要這麼做，請按一下其中一個具有資料夾權限的群組（或運算子），然後從下拉式清單中選取新群組（或新運算子）:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **授權群組或營運商**。 若要這麼做，請按一 **[!UICONTROL Add]** 下按鈕，並選取您要為此資料夾指派授權的群組或運算子。
* **禁止群組或營運商**。 要執行此操作，請單 **[!UICONTROL Delete]** 擊並選擇要從中刪除此資料夾授權的組或運算子。
* **選擇指派給群組或運算子的權限**。 若要這麼做，請按一下相關的群組或運算子，然後選取您要授與的存取權，並取消選取其他的存取權。

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 傳播權限 {#propagate-permissions}

您可以傳播授權和訪問權限。 若要這麼做，請選取資 **[!UICONTROL Propagate]** 料夾屬性中的選項。

然後，在此窗口中定義的授權將應用於當前節點的所有子資料夾。 然後，您可以對每個子資料夾超載這些授權。

>[!NOTE]
>
>清除資料夾的此選項不會自動清除子資料夾的選項。 您必須明確清除每個子資料夾。

### 授予所有運算子的存取權 {#grant-access-to-all-operators}

在標籤 **[!UICONTROL Security]** 中，如果選取 **[!UICONTROL System folder]** 了選項，所有運算子都可存取此資料，不論其權限為何。 如果清除此選項，您必須將運算子（或其群組）明確新增至授權清單，以便其擁有存取權。

![](assets/s_ncs_user_folder_properties_security03b.png)

## 資料夾和檢視 {#folders-and-views}

### 關於資料夾 {#about-folders}

資料夾是Adobe Campaign樹狀結構中的節點。 通過按一下右鍵樹，可通過菜單建立這些 **[!UICONTROL Add new folder]** 節點。 依預設，第一個功能表可讓您新增與目前內容對應的資料夾。

![](assets/s_ncs_user_add_folder_in_tree.png)

您可以授予這些資料夾的權限，就像對樹的所有其他資料夾一樣。 請參閱 [資料夾存取管理](#folder-access-management)。

### 關於視圖 {#about-views}

此外，您還可以建立檢視，以限制資料存取，並組織樹狀結構的內容以符合您的需求。 然後，您可以指派檢視的權限。

視圖是一個資料夾，它顯示物理上儲存在同一類型的一個或多個其他資料夾中的記錄。 例如，如果您建立的「促銷活動」資料夾是檢視，則預設會顯示資料庫中顯示的所有促銷活動，無論其來源為何。 然後可以篩選此資料。

將資料夾轉換為視圖時，與資料庫中存在的資料夾類型相對應的所有資料都會顯示在視圖中，而與保存資料夾無關。 然後，您可以篩選它，以限制顯示的資料清單。

>[!IMPORTANT]
>
>這些視圖包含資料並提供對其的訪問，但資料不實際儲存在視圖資料夾中。 運算子必須擁有資料來源資料夾中所需動作的適當權限（至少是讀取存取）。
>
>要在不授予對其源資料夾訪問權限的情況下授予對視圖的訪問權限，只要不授予對源資料夾父節點的讀訪問權限即可。

要區分視圖和資料夾，每個視圖的名稱以不同的顏色（深青色）顯示。

![](assets/s_ncs_user_view_name_color.png)

### 添加資料夾和建立視圖 {#adding-folders-and-creating-views}

在以下範例中，我們將建立新資料夾以顯示特定資料：

1. 建立新的類 **[!UICONTROL Deliveries]** 型檔案夾，並將它命名為 **Deliveries France**。
1. 按一下右鍵此資料夾並選擇 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_add_folder_exple.png)

1. 在頁籤 **[!UICONTROL Restriction]** 中，選擇 **[!UICONTROL This folder is a view]**。 然後會顯示資料庫中的所有傳送。

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 從視窗中間區段的查詢編輯器定義傳送篩選條件： 接著會顯示與已定義篩選器對應的促銷活動。

   >[!NOTE]
   >
   >此部分顯示查詢 [編輯器](../../platform/using/about-queries-in-campaign.md)。

   使用下列篩選條件：

![](assets/s_ncs_user_add_folder_exple00.png)

檢視中將顯示下列傳送：

![](assets/s_ncs_user_add_folder_exple02.png)
