---
product: campaign
title: 開始使用Campaign運算子
description: 了解如何建立和管理行銷活動使用者
feature: Access Management
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 2%

---

# 建立及管理操作者 {#operators}

![](../../assets/common.svg)

## 開始使用Campaign運算子  {#about-operators}

運算子是具有登入及執行動作權限的Adobe Campaign使用者。

依預設，運算子會儲存在 **[!UICONTROL Administration > Access management > Operators]** 節點。

![](assets/s_ncs_user_list_operators.png)

可以手動建立運算子，或在現有LDAP目錄上映射運算子。

建立運算子的完整程式如下所述： [本頁](#creating-an-operator).

如需Adobe Campaign和LDAP整合的詳細資訊，請參閱 [本頁](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>運算子必須連結至安全區域才能登入執行個體。 如需Adobe Campaign安全區的詳細資訊，請參閱 [本頁](../../installation/using/security-zones.md).

使用者也可以使用其Adobe ID直接連線至Adobe Campaign。 如需關於此項目的詳細資訊，請參閱此[頁面](../../integrations/using/about-adobe-id.md)。

## 建立運算子 {#creating-an-operator}

若要建立新運算子並授予權限，請遵循下列步驟：

1. 按一下 **[!UICONTROL New]** 按鈕，然後輸入新運算子的詳細資訊。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定 **[!UICONTROL Identification parameters]** 使用者：其登錄名、密碼和名稱。 運算子將使用登入和密碼來登入Adobe Campaign。 使用者登入後，可透過 **[!UICONTROL Tools > Change password]** 功能表。 運算子的電子郵件至關重要，因為它可讓運算子接收通知，例如在處理核準時。

   本節也可讓您將運算子連結至組織實體。 有關詳細資訊，請參閱 [本頁](../../distributed/using/about-distributed-marketing.md).

1. 選取授予運算子的權限，位於 **[!UICONTROL Operator access rights]** 區段。

   若要指派運算子的權限，請按一下 **[!UICONTROL Add]** 按鈕，然後從可用組清單中選擇一組操作符：

   ![](assets/s_ncs_user_permissions_operators.png)

   您也可以選取一或多個指定權限(請參閱 [已命名的權限](#named-rights))。 若要這麼做，請按一下 **[!UICONTROL Folder]** 欄位，然後選取 **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   選取要指派的群組和/或已命名的權限，然後按一下 **[!UICONTROL OK]** 以驗證。

1. 按一下 **[!UICONTROL Ok]** 若要建立運算子：會將設定檔新增至現有運算子清單。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>您可以建立新的運算子資料夾，以根據您的需求組織運算子。 要執行此操作，請按一下右鍵運算子資料夾並選擇 **[!UICONTROL Add an 'Operators' folder]**.

建立運算子的設定檔後，您就可以新增或更新其資訊。 若要這麼做，請按一下 **[!UICONTROL Edit]** 標籤。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>此 **[!UICONTROL Session timeout]** 欄位可讓您調整FDA工作階段逾時前的延遲。 有關詳細資訊，請參閱 [關於同盟資料存取](../../installation/using/about-fda.md).

## 定義運算子的時區 {#time-zone-of-the-operator}

在 **[!UICONTROL General]** 索引標籤，您可以選取運算子的時區。 依預設，運算子會在伺服器時區中運作。 不過，您可以使用下拉式清單選取其他時區。

時區的設定如下所述： [本頁](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>不同時區內的協作需要以UTC儲存日期。 在下列情況下，日期會在適當的時區中轉換：當日期顯示在使用者時區中時，當檔案匯入和匯出時，當排程電子郵件傳送時，當活動排程在工作流程中時（排程器、等待、時間限制等）
>
>Adobe Campaign檔案的相關章節列出了與這些背景有關的限制和建議。

此外， **[!UICONTROL Regional settings]** 下拉式清單可讓您選取顯示日期和數字的格式。

## 新增權限 {#access-rights-options}

使用 **[!UICONTROL Access rights]** 頁簽來更新連結到運算子的組和命名權限。

![](assets/operator_profile_security_options.png)

此 **[!UICONTROL Edit the access parameters...]** 連結可讓您存取下列選項：

* 此 **[!UICONTROL Disable account]** 選項可讓您停用運算子的帳戶：此使用者將不再存取Adobe Campaign。

   >[!NOTE]
   >
   >即使其帳戶已停用，運算子仍可從Campaign接收警報或通知。 若要停止傳送Campaign通知給此運算子，Adobe建議您從其設定檔中移除電子郵件地址。

* 此 **[!UICONTROL Forbid access from the rich client]** 選項，限制使用Adobe Campaign [網路存取](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 或透過API:無法再存取Adobe Campaign用戶端主控台。
* 可以將安全區連結到操作員。 如需詳細資訊，請參閱[此頁面](../../installation/using/security-zones.md)。
* 您也可以使用適當的連結來定義受信任的IP遮罩。

   如果運算子的IP位址在此清單中，該運算子便能直接連線至Adobe Campaign，而不需輸入密碼。

   您也可以指定一組IP位址，這些位址將獲授權不使用密碼即可連線，如下列範例：

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >若要確保平台存取安全，您必須謹慎使用此選項。

* 此 **[!UICONTROL Restrict to information found in sub-folders of:]** 選項可讓您限制屬於資料夾運算子的權限。 用戶只能看到此選項中指定的節點的子資料夾：

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >這是非常嚴格的限制，必須小心使用。 以此類權限登錄的運算子只能查看指定資料夾的內容，並且無法通過資源管理器訪問樹的任何其他節點。 不過，根據此運算子可存取的功能(例如：工作流程)，則使用者可顯示通常儲存在無法存取之節點中的資料。

### 檢查設定 {#check-settings}

此 **[!UICONTROL Audit]** 標籤，即可檢視與運算子相關的資訊。 系統會根據運算子干預區域中定義的設定，自動將各種標籤新增至。

您可以存取：

* 連結到運算子的資料夾權限清單。

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >有關詳細資訊，請參閱 [資料夾存取管理](#folder-access-management).

* 操作員批准日誌。

   ![](assets/operator_profile_validations.png)

* 他們所訂閱的論壇清單。
* 日曆中的事件。
* 分配給它們的任務清單。

## 預設運算子 {#default-operators}

Adobe Campaign使用技術運算子，預設會設定設定檔：管理員（「管理員」）、帳單（「帳單」）、監控、Web應用程式代理(「webapp」)等 其中有些取決於平台上安裝的應用程式和選項：例如，「central」和「local」運算子只有在安裝了「Distributed Marketing」選項時才會顯示。

>[!IMPORTANT]
>
>當平台傳回資訊訊息時，預設會通知這些技術營運商。 我們強烈建議為使用者提供聯絡電子郵件。
>
>為確保Web應用程式正常運作，我們也建議不要為「webapp」運算子定義特定的區域設定。

依預設，「webapp」技術運算子具有命名的「管理」權限，這可能會導致安全風險。 若要解決此問題，建議您移除此權限。 操作步驟：

1. 從 **[!UICONTROL Administration > Access management > Named rights]** 節點，按一下 **[!UICONTROL New]** 建立權限並將其命名為WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   在 [已命名的權限](#named-rights) 區段。

1. 從 **[!UICONTROL Administration > Access management > Operators]** 節點，選擇Web應用程式代理運算子(「webapp」)。

   選取 **[!UICONTROL Edit]** ，然後 **[!UICONTROL Access rights]** 頁簽，並從清單中刪除名為的ADMINISTRATION。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   按一下 **[!UICONTROL Add]** 並選取您剛建立的WEBAPP，然後儲存您的變更。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 為與此運算子相關的資料夾（主要是「收件者」資料夾）指派「webapp」運算子讀取和寫入資料存取權限。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   有關修改樹資料夾的權限的詳細資訊，請參閱 [資料夾存取管理](#folder-access-management) 區段。

>[!NOTE]
>
>如需安全性指引的詳細資訊，請參閱 [Adobe Campaign安全性配置檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html).
