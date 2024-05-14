---
product: campaign
title: 開始使用Campaign運運算元
description: 瞭解如何建立和管理Campaign使用者
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: e1a085384fb27ec165c487c112fbc70fe9738d9e
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 2%

---

# 建立及管理操作者 {#operators}

>[!CAUTION]
>
>從Campaign Classicv7.3.1開始，所有運運算元都應該使用 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"} 以連線至Campaign。
>
>為了強化安全性和驗證程式，Adobe Campaign強烈建議您將所有現有的操作員驗證模式從登入/密碼原生驗證移轉至AdobeIdentity Management系統(IMS)。 瞭解如何在中移轉您的操作員 [此頁面](../../technotes/using/migrate-users-to-ims.md).
> 
>移轉後，請注意下一節不再適用。  瞭解如何在中使用Adobe IMS設定許可權 [Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=zh-Hant){target="_blank"}.


## 開始使用Campaign運運算元  {#about-operators}

運運算元是有許可權登入及執行動作的Adobe Campaign使用者。

依預設，運運算元儲存在 **[!UICONTROL Administration > Access management > Operators]** 節點。

![](assets/s_ncs_user_list_operators.png)

運運算元可以手動建立，或對應至現有的LDAP目錄。

建立運運算元的完整程式如下所述： [此頁面](#creating-an-operator).

如需Adobe Campaign和LDAP整合的詳細資訊，請參閱 [此頁面](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>運運算元必須連結至安全區域，才能登入執行個體。 如需Adobe Campaign中安全性區域的詳細資訊，請參閱 [此頁面](../../installation/using/security-zones.md).

使用者也可以使用其Adobe ID直接連線至Adobe Campaign。 如需關於此項目的詳細資訊，請參閱此[頁面](../../integrations/using/about-adobe-id.md)。

## 建立運運算元 {#creating-an-operator}

若要建立新運運算元並授與許可權，請遵循下列步驟：

1. 按一下 **[!UICONTROL New]** 按鈕，並輸入新運運算元的詳細資訊。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定 **[!UICONTROL Identification parameters]** 使用者的名稱：其登入名稱、密碼和名稱。 操作員將使用登入和密碼來登入Adobe Campaign。 使用者登入後，他們便可以透過 **[!UICONTROL Tools > Change password]** 功能表。 操作員的電子郵件至關重要，因為它可讓操作員接收通知，例如在處理核準時。

   此區段也可讓您將運運算元連結至組織實體。 有關詳細資訊，請參閱 [此頁面](../../distributed/using/about-distributed-marketing.md).

1. 選取授與運運算元的許可權，在 **[!UICONTROL Operator access rights]** 區段。

   若要指派許可權給運運算元，請按一下 **[!UICONTROL Add]** 按鈕時，請從可用群組清單中選取一組運運算元：

   ![](assets/s_ncs_user_permissions_operators.png)

   您也可以選取一或多個已命名的許可權(請參閱 [已命名的許可權](#named-rights))。 若要這麼做，請按一下右側的箭頭 **[!UICONTROL Folder]** 欄位，然後選取 **[!UICONTROL Named rights]**：

   ![](assets/s_ncs_user_rights_operators.png)

   選取要指派的群組及/或已命名許可權，然後按一下 **[!UICONTROL OK]** 以進行驗證。

1. 按一下 **[!UICONTROL Ok]** 建立運運算元：設定檔會新增至現有運運算元的清單中。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>您可以建立新的運運算元資料夾，根據您的需求組織運運算元。 若要這麼做，請以滑鼠右鍵按一下運運算元資料夾，然後選取 **[!UICONTROL Add an 'Operators' folder]**.

建立運運算元的設定檔後，您就可以新增或更新其資訊。 若要這麼做，請按一下 **[!UICONTROL Edit]** 標籤。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>此 **[!UICONTROL Session timeout]** 欄位可讓您調整FDA工作階段逾時前的延遲。 有關詳細資訊，請參閱 [關於同盟資料存取](../../installation/using/about-fda.md).

## 定義運運算元的時區 {#time-zone-of-the-operator}

在 **[!UICONTROL General]** 標籤中，您可以選取運運算元的時區。 依預設，運運算元在伺服器時區中運作。 不過，您也可以使用下拉式清單選取其他時區。

時區的設定詳見 [此頁面](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>不同時區內的合作需要以UTC儲存日期。 日期會在下列內容的適當時區中轉換：當日期以使用者時區顯示時、當檔案匯入和匯出時、當排程電子郵件傳送時、當活動在工作流程中排程時（排程器、等待、時間限制等）
>
>連結至這些內容的限制和建議會顯示在Adobe Campaign檔案的相關章節。

此外， **[!UICONTROL Regional settings]** 下拉式清單可讓您選取顯示日期和數字的格式。

## 新增許可權 {#access-rights-options}

使用 **[!UICONTROL Access rights]** 索引標籤以更新連結至運運算元的群組和已命名許可權。

![](assets/operator_profile_security_options.png)

此 **[!UICONTROL Edit the access parameters...]** 連結可讓您存取下列選項：

* 此 **[!UICONTROL Disable account]** 選項可讓您停用操作員的帳戶：此使用者將不再存取Adobe Campaign。

  >[!NOTE]
  >
  >即使其帳戶已停用，操作員仍可接收來自Campaign的警報或通知。 若要停止傳送Campaign通知給此操作員，Adobe建議您從他們的設定檔中移除電子郵件地址。

* 此 **[!UICONTROL Forbid access from the rich client]** 選項可讓您限制使用Adobe Campaign至 [網頁存取](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 或透過API：無法再存取Adobe Campaign使用者端主控台。
* 您可以將安全區域連結到操作員。 如需詳細資訊，請參閱[此頁面](../../installation/using/security-zones.md)。
* 您也可以使用適當的連結，定義信任的IP遮罩。

  如果運運算元的IP位址在此清單中，運運算元便能連線至Adobe Campaign，不必輸入密碼。

  您也可以指定一組IP位址，這些位址將授權在不使用密碼的情況下進行連線，如下列範例所示：

  ![](assets/operator_trustip.png)

  >[!NOTE]
  >
  >為了確保您平台的存取安全，使用此選項時務必謹慎。

* 此 **[!UICONTROL Restrict to information found in sub-folders of:]** 選項可讓您限制歸屬於資料夾運運算元的許可權。 只有使用者可看見此選項中所指定節點的子資料夾：

  ![](assets/s_ncs_user_restrictions_operators.png)

  >[!IMPORTANT]
  >
  >這是非常嚴格的限制，必須謹慎使用。 以此類許可權登入的運運算元只能看到指定資料夾的內容，無法透過瀏覽器存取樹狀結構的任何其他節點。 不過，根據此運運算元可存取的功能（例如：工作流程），使用者可以顯示通常儲存在無法存取的節點中的資料。

### 檢查設定 {#check-settings}

此 **[!UICONTROL Audit]** 索引標籤可讓您檢視運運算元的相關資訊。 各種標籤會根據運運算元的介入區域中定義的設定自動新增到。

您可以存取：

* 連結至運運算元的資料夾上的許可權清單。

  ![](assets/operator_folder_permissions.png)

  >[!NOTE]
  >
  >有關詳細資訊，請參閱 [資料夾存取管理](#folder-access-management).

* 操作員核准記錄。

  ![](assets/operator_profile_validations.png)

* 他們訂閱的討論區清單。
* 行事曆中的活動。
* 指派給他們的任務清單。

## 預設運運算元 {#default-operators}

Adobe Campaign會使用具有預設設定之設定檔的技術操作員：管理員（「管理員」）、帳單（「帳單」）、監控、Web應用程式代理程式(「webapp」)等。 其中有部分取決於平台上安裝的應用程式和選項：例如，「中央」和「本機」運運算元，只有在安裝了「分散式行銷」選項時才會顯示。

>[!IMPORTANT]
>
>當平台傳回資訊訊息時，預設會通知這些技術操作者。 我們強烈建議您向他們提供聯絡電子郵件。
>
>為確保Web應用程式正常運作，我們也建議不要為「webapp」運運算元定義特定的地區設定。

依預設，「webapp」技術操作員具有指定的ADMINISTRATION許可權，這可能會導致安全性風險。 若要修正此問題，建議您移除此權利。 操作步驟：

1. 從 **[!UICONTROL Administration > Access management > Named rights]** 節點，按一下 **[!UICONTROL New]** 以建立許可權並將其命名為WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   已命名的許可權詳見 [已命名的許可權](#named-rights) 區段。

1. 從 **[!UICONTROL Administration > Access management > Operators]** 節點，選取Web應用程式代理程式運運算元(&#39;webapp&#39;)。

   選取 **[!UICONTROL Edit]** 標籤，然後 **[!UICONTROL Access rights]** 標籤並從清單中刪除名為許可權的ADMINISTRATION。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   按一下 **[!UICONTROL Add]** 並選取您剛建立的WEBAPP，然後儲存變更。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 指派「webapp」運運算元對與此運運算元相關的資料夾（主要是「收件者」資料夾）的讀寫資料存取許可權。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   有關修改樹狀結構資料夾許可權的詳情，請參閱 [資料夾存取管理](#folder-access-management) 區段。

>[!NOTE]
>
>如需安全性方針的詳細資訊，請參閱 [Adobe Campaign安全性設定檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html).
