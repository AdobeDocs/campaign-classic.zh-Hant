---
product: campaign
title: 開始使用活動操作員
description: 瞭解如何建立和管理市場活動用戶
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 2%

---

# 建立及管理操作者 {#operators}

![](../../assets/common.svg)

## 開始使用活動操作員  {#about-operators}

操作員是具有登錄和執行操作權限的Adobe Campaign用戶。

預設情況下，運算子儲存在 **[!UICONTROL Administration > Access management > Operators]** 的下界。

![](assets/s_ncs_user_list_operators.png)

可以手動建立或映射現有LDAP目錄上的運算子。

建立運算子的完整過程如中所述 [此頁](#creating-an-operator)。

有關Adobe Campaign和LDAP整合的詳細資訊，請參閱 [此頁](../../installation/using/connecting-through-ldap.md)。

>[!IMPORTANT]
>
>操作員需要連結到安全區域才能登錄到實例。 有關Adobe Campaign安全區的詳細資訊，請參閱 [此頁](../../installation/using/security-zones.md)。

用戶還可以使用自己的Adobe ID直接連接到Adobe Campaign。 如需關於此項目的詳細資訊，請參閱此[頁面](../../integrations/using/about-adobe-id.md)。

## 建立運算子 {#creating-an-operator}

要建立新操作員並授予權限，請執行以下步驟：

1. 按一下 **[!UICONTROL New]** 的子菜單。

   ![](assets/s_ncs_user_operator_new.png)

1. 指定 **[!UICONTROL Identification parameters]** 的下界：其登錄名、密碼和名稱。 操作員將使用登錄名和密碼登錄Adobe Campaign。 用戶登錄後，他們可以通過 **[!UICONTROL Tools > Change password]** 的子菜單。 操作員的電子郵件至關重要，因為它使操作員能夠接收通知，例如在處理批准時。

   此部分還允許您將操作員連結到組織實體。 有關詳細資訊，請參閱 [此頁](../../distributed/using/about-distributed-marketing.md)。

1. 選擇在 **[!UICONTROL Operator access rights]** 的子菜單。

   要為操作員分配權限，請按一下 **[!UICONTROL Add]** 按鈕，然後從可用組清單中選擇一組運算子：

   ![](assets/s_ncs_user_permissions_operators.png)

   您還可以選擇一個或多個命名權限(請參閱 [命名權限](#named-rights))。 要執行此操作，請按一下 **[!UICONTROL Folder]** ，然後選擇 **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   選擇要分配的組和/或命名權限，然後按一下 **[!UICONTROL OK]** 驗證。

1. 按一下 **[!UICONTROL Ok]** 要建立運算子：配置檔案將添加到現有運算子清單中。

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>通過建立新的運算子資料夾，可以根據您的要求組織運算子。 為此，請按一下右鍵運算子資料夾並選擇 **[!UICONTROL Add an 'Operators' folder]**。

建立操作員的配置檔案後，您可以添加或更新其資訊。 要執行此操作，請按一下 **[!UICONTROL Edit]** 頁籤。

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>的 **[!UICONTROL Session timeout]** 欄位允許您調整FDA會話超時之前的延遲。 有關此內容的詳細資訊，請參閱 [關於聯合資料存取](../../installation/using/about-fda.md)。

## 定義運算子的時區 {#time-zone-of-the-operator}

在 **[!UICONTROL General]** 頁籤。 預設情況下，運算子在伺服器時區中工作。 但是，可以使用下拉清單選擇另一個時區。

有關時區的配置，請參見 [此頁](../../installation/using/time-zone-management.md)。

>[!NOTE]
>
>不同時區內的協作需要以UTC形式儲存日期。 在以下上下文中在相應的時區轉換日期：在用戶時區中顯示日期時，在導入和導出檔案時，在計畫電子郵件傳遞時，在工作流中安排活動時（計畫程式、等待、時間約束等）。
>
>與這些情況相關的制約因素和建議載於Adobe Campaign檔案的有關章節。

另外， **[!UICONTROL Regional settings]** 下拉清單允許您選擇顯示日期和數字的格式。

## 添加權限 {#access-rights-options}

使用 **[!UICONTROL Access rights]** 頁籤以更新連結到運算子的組和命名權限。

![](assets/operator_profile_security_options.png)

的 **[!UICONTROL Edit the access parameters...]** 連結允許您訪問以下選項：

* 的 **[!UICONTROL Disable account]** 選項，您可以禁用操作員的帳戶：此用戶將不再訪問Adobe Campaign。

   >[!NOTE]
   >
   >即使其帳戶被禁用，操作員仍可以從市場活動接收警報或通知。 要停止向此操作員發送市場活動通知，Adobe建議您從其配置檔案中刪除電子郵件地址。

* 的 **[!UICONTROL Forbid access from the rich client]** 選項，您可以將Adobe Campaign的使用限制為 [Web訪問](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 或通過API:對Adobe Campaign客戶端控制台的訪問不再可用。
* 可以將安全區域與操作員連結。 如需詳細資訊，請參閱[此頁面](../../installation/using/security-zones.md)。
* 您還可以使用相應的連結定義受信任的IP掩碼。

   如果IP地址在此清單中，則操作員將能夠連接到Adobe Campaign，而無需輸入密碼。

   您還可以指定一組IP地址，這些地址將被授權在沒有密碼的情況下進行連接，如以下示例中所示：

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >要保證對平台的安全訪問，必須謹慎使用此選項。

* 的 **[!UICONTROL Restrict to information found in sub-folders of:]** 選項，用於限制屬於資料夾運算子的權限。 只有此選項中指定的節點的子資料夾才對用戶可見：

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >這是一個非常嚴格的限制，必須謹慎使用。 使用此類權限登錄的操作員只能查看指定資料夾的內容，並且無法通過瀏覽器訪問樹的任何其他節點。 但是，根據操作員可以訪問的功能(例如：工作流)，用戶可以顯示通常儲存在無法訪問的節點中的資料。

### 檢查設定 {#check-settings}

的 **[!UICONTROL Audit]** 頁籤中，您可以查看與運算子相關的資訊。 根據在操作員干預區域中定義的設定自動添加各個頁籤。

您可以訪問：

* 連結到運算子的資料夾的權限清單。

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >有關此內容的詳細資訊，請參閱 [資料夾訪問管理](#folder-access-management)。

* 操作員批准日誌。

   ![](assets/operator_profile_validations.png)

* 他們訂閱的討論論壇清單。
* 日曆中的事件。
* 分配給它們的任務清單。

## 預設運算子 {#default-operators}

Adobe Campaign使用預設配置的技術操作員：管理員(&#39;admin&#39;)、計費(&#39;billing&#39;)、監視、Web應用程式代理(&#39;webapp&#39;)等。 其中一些取決於平台上安裝的應用程式和選項：例如，只有安裝了「分佈式營銷」選項，「central」和「local」運算子才可見。

>[!IMPORTANT]
>
>當平台返回資訊消息時，預設情況下會通知這些技術操作員。 我們強烈建議為他們提供聯繫電子郵件。
>
>為確保Web應用程式正常運行，我們還建議不要為「webapp」操作員定義特定的區域設定。

預設情況下，「webapp」技術操作員具有命名為ADMINISTRATION的權限，這會導致安全風險。 要解決此問題，建議刪除此權限。 操作步驟：

1. 從 **[!UICONTROL Administration > Access management > Named rights]** 節點，按一下 **[!UICONTROL New]** 建立權限並將其命名為WEBAPP。

   ![](assets/s_ncs_default_operators_webapp_right.png)

   命名權限在 [命名權限](#named-rights) 的子菜單。

1. 從 **[!UICONTROL Administration > Access management > Operators]** 節點，選擇Web應用程式代理運算子(「webapp」)。

   選擇 **[!UICONTROL Edit]** ，則 **[!UICONTROL Access rights]** 頁籤，然後從清單中刪除名為右的ADMINISTRATION。

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   按一下 **[!UICONTROL Add]** 並選擇您剛建立的WEBAPP權限，然後保存您所做的更改。

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 為與此操作員（主要是「收件人」資料夾）相關的資料夾分配「webapp」操作員讀取和寫入資料存取權限。

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   修改樹資料夾的權限在 [資料夾訪問管理](#folder-access-management) 的子菜單。

>[!NOTE]
>
>有關安全指南的詳細資訊，請參閱 [Adobe Campaign安全配置核對表](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。
