---
product: campaign
title: CRM連接器資料同步
description: 在Campaign和您的CRM之間管理資料
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 0%

---

# 在Campaign和CRM {#data-synchronization}之間同步資料

Adobe Campaign和CRM之間的資料同步是透過專用的工作流程活動執行：[CRM連接器](../../workflow/using/crm-connector.md)。

例如，若要將Microsoft Dynamics資料匯入Adobe Campaign，請建立下列類型的工作流程：

![](assets/crm_connectors_msdynamics_07.png)

此工作流程會透過Microsoft Dynamics匯入聯絡人、將其與現有的Adobe Campaign資料同步、刪除重複的聯絡人，以及更新Adobe Campaign資料庫。

**[!UICONTROL CRM Connector]**&#x200B;活動需要配置以同步資料。

![](assets/crm_connectors_msdynamics_08.png)

透過此活動，您可以：

* 從CRM匯入 — [了解更多](#importing-from-the-crm)
* 匯出至CRM - [了解更多](#exporting-to-the-crm)
* 導入在CRM中刪除的對象 — [了解更多](#importing-objects-deleted-in-the-crm)
* 刪除CRM中的對象 — [了解更多](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

選擇與要配置同步的CRM匹配的外部帳戶，然後選擇要同步的對象：帳戶、機會、銷售機會、聯繫人等

![](assets/crm_task_select_obj.png)

此活動的設定取決於要執行的程式。 以下詳細說明各種配置。

## 從CRM {#importing-from-the-crm}導入

若要透過Adobe Campaign中的CRM匯入資料，您需要建立下列類型的工作流程：

![](assets/crm_wf_import.png)

對於匯入活動，**[!UICONTROL CRM Connector]**&#x200B;活動配置步驟為：

1. 選擇&#x200B;**[!UICONTROL Import from the CRM]**&#x200B;操作。
1. 轉至&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉清單，並選擇進程所關注的對象。 此物件與連接器配置期間在Adobe Campaign中建立的其中一個表重合。
1. 前往&#x200B;**[!UICONTROL Remote fields]**&#x200B;區段，並輸入要匯入的欄位。

   若要新增欄位，請按一下工具列中的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;圖示。

   ![](assets/crm_task_import_add_field.png)

   如有必要，請透過&#x200B;**[!UICONTROL Conversion]**&#x200B;欄的下拉式清單變更資料格式。 可能的轉換類型在[資料格式](#data-format)中詳細說明。

   >[!IMPORTANT]
   >
   >在CRM和Adobe Campaign中，連結物件時，CRM中記錄的識別碼是必填的。 當核准方塊時，就會自動新增。
   >
   >對於增量資料匯入，CRM端的上次修改日期也是必要項目。

1. 您也可以根據需求篩選要匯入的資料。 要執行此操作，請按一下&#x200B;**[!UICONTROL Edit the filter...]**&#x200B;連結。

   在下列範例中，Adobe Campaign只會匯入自2012年11月1日以來已記錄某些活動的連絡人。

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >[篩選資料](#filtering-data)中詳細說明了連結到資料篩選模式的限制。

1. **[!UICONTROL Use automatic index...]**&#x200B;選項可讓您根據日期和上次修改，自動管理CRM和Adobe Campaign之間的增量物件同步。

   有關詳細資訊，請參閱[變數管理](#variable-management)。

### 管理變數{#variable-management}

啟用&#x200B;**[!UICONTROL Automatic index]**&#x200B;選項，僅收集自上次導入以來修改的對象。

![](assets/crm_task_import_option.png)

預設情況下，上次同步的日期將儲存在配置窗口中指定的選項中：**LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**。

>[!NOTE]
>
>此注釋僅適用於一般&#x200B;**[!UICONTROL CRM Connector]**&#x200B;活動。 對於其他CRM活動，程式會自動執行。
>
>必須在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下手動建立並填入此選項。 它必須是文字選項，其值必須符合下列格式：**yyyy/MM/dd hh:mm:ss**。
> 
>您需要手動更新此選項，才能進行任何進一步匯入。

您可以指定要考慮的遠端CRM欄位，以識別最近的變更。

預設會使用下列欄位（依指定順序）:

* 對於Microsoft Dynamics:**在**&#x200B;上修改，
* 對於Salesforce.com:**LastModifiedDate**, **SystemModstamp**。

啟用&#x200B;**[!UICONTROL Automatic index]**&#x200B;選項會產生三個變數，這些變數可透過&#x200B;**[!UICONTROL JavaScript code]**&#x200B;類型活動用於同步工作流程中。 這些活動包括：

* **vars.crmOptionName**:代表包含上次匯入日期之選項的名稱。
* **vars.crmStartImport**:表示上次資料恢復的開始日期（包括）。
* **vars.crmEndDate**:代表上次資料恢復的結束日期（已排除）。

   >[!NOTE]
   >
   >這些日期會以下列格式顯示：**yyyy/MM/dd hh:mm:ss**。

### 篩選資料 {#filtering-data}

為了確保對各種CRM進行有效操作，需使用以下規則建立篩選器：

* 每個篩選層級只能使用一種運算子。
* 不支援AND NOT運算子。
* 比較可能只涉及空值（「為空」/「非空」類型）或數字。 這表示會評估值（右側欄），此評估的結果必須為數字。 因此不支援JOIN類型比較。
* 右側欄中的值會以JavaScript評估。
* 不支援連接比較。
* 左欄中的運算式必須是欄位。 它不能是數個運算式、數字等的組合。

例如，下列篩選條件對CRM匯入無效，因為OR運算子放置在與運算子相同的層級：

* OR運算子放置在與運算子相同的層級
* 會對文字字串進行比較

![](assets/crm_import_wrong_filter.png)

### 按{#order-by}排序

在Microsoft Dynamics和Salesforce.com中，您可以按升序或降序排序要導入的遠程欄位。

要執行此操作，請按一下&#x200B;**[!UICONTROL Order by]**&#x200B;連結，並將欄新增至清單。

清單中的欄順序是排序順序：

![](assets/crm_import_order.png)

### 記錄標識{#record-identification}

與其匯入CRM中包含的元素（且可能經過篩選），您可以使用工作流程中預先計算的母體。

要執行此操作，請選擇&#x200B;**[!UICONTROL Use the population calculated upstream]**&#x200B;選項並指定包含遠程標識符的欄位。

然後選取您要匯入的入站母體欄位，如下所示：

![](assets/crm_wf_import_calculated_population.png)

## 導出到CRM {#exporting-to-the-crm}

將Adobe Campaign資料匯出至CRM可讓您將整個內容複製至CRM資料庫。

若要將資料匯出至CRM，您需要建立下列類型的工作流程：

![](assets/crm_export_diagram.png)

對於匯出，請將下列設定套用至&#x200B;**[!UICONTROL CRM Connector]**&#x200B;活動：

1. 選擇&#x200B;**[!UICONTROL Export to CRM]**&#x200B;操作。
1. 轉至&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉清單，並選擇進程所關注的對象。 此物件與連接器配置期間在Adobe Campaign中建立的其中一個表重合。

   >[!IMPORTANT]
   >
   >**[!UICONTROL CRM Connector]**&#x200B;活動的匯出函式可以在CRM端插入或更新欄位。 若要啟用CRM中的欄位更新，您必須指定遠端表格的主要索引鍵。 如果缺少金鑰，則會插入資料（而非更新）。

1. 在&#x200B;**[!UICONTROL Mapping]**&#x200B;區段中，指定要匯出的欄位及其在CRM中的對應。

   ![](assets/crm_export_config.png)

   若要新增欄位，請按一下工具列中的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;圖示。

   >[!NOTE]
   >
   >對於指定欄位，如果CRM端未定義相符項目，則無法更新值：會直接插入CRM中。

   如有必要，請透過&#x200B;**[!UICONTROL Conversion]**&#x200B;欄的下拉式清單變更資料格式。 可能的轉換類型在[資料格式](#data-format)中詳細說明。

   >[!NOTE]
   >
   >要導出的記錄清單和導出結果將保存在臨時檔案中，該檔案在工作流完成或重新啟動之前始終可訪問。 這可讓您在發生錯誤時重新啟動程式，而不會執行多次匯出相同記錄或遺失資料的風險。

## 其他配置 {#additional-configurations}

### 資料格式{#data-format}

將資料格式匯入CRM時或從CRM匯入時，您可以即時轉換資料格式。

若要這麼做，請選取要在相符欄中套用的轉換。

![](assets/crm_task_import.png)

**[!UICONTROL Default]**&#x200B;模式會套用自動資料轉換，在大多數情況下等於資料的複製/貼上。 但是會套用時區管理。

其他可能的轉換包括：

* **[!UICONTROL Date only]**:此模式會刪除「日期+時間」類型欄位。
* **[!UICONTROL Without time offset]**:此模式取消在預設模式中應用的時區管理。
* **[!UICONTROL Copy/Paste]**:此模式使用字串等原始資料（無轉換）。

### 處理{#error-processing}時出錯

在資料匯入或匯出的架構中，您可以將特定程式套用至錯誤和拒絕。 要執行此操作，請在&#x200B;**[!UICONTROL Behavior]**&#x200B;標籤中選取&#x200B;**[!UICONTROL Process rejects]**&#x200B;和&#x200B;**[!UICONTROL Process errors]**&#x200B;選項。

![](assets/crm_export_options.png)

這些選項會放置相符的輸出轉變。

![](assets/crm_export_transitions.png)

然後，放置與要應用的流程相關的活動。

若要處理例項的錯誤，您可以新增等待方塊並排程重試。

系統會以其錯誤碼和相關訊息收集拒絕，這表示您可以設定拒絕的追蹤，以最佳化同步程式。

>[!NOTE]
>
>即使未啟用&#x200B;**[!UICONTROL Process rejects]**&#x200B;選項，也會為每個包含錯誤代碼和消息的已拒絕列生成警告。

**[!UICONTROL Reject]**&#x200B;輸出轉變可讓您存取包含與錯誤訊息和程式碼相關的特定欄的輸出架構。 對於Salesforce.com，此列為&#x200B;**errorSymbol**（錯誤符號，與錯誤代碼不同）, **errorMessage**（錯誤上下文的說明）。

## 導入在CRM {#importing-objects-deleted-in-the-crm}中刪除的對象

若要啟用廣泛資料同步程式的設定，您可以將CRM中刪除的物件匯入Adobe Campaign。

若要這麼做，請套用下列步驟：

1. 選擇&#x200B;**[!UICONTROL Import objects deleted in the CRM]**&#x200B;操作。
1. 轉至&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉清單，並選擇進程所關注的對象。 此物件與連接器配置期間在Adobe Campaign中建立的其中一個表重合。
1. 在&#x200B;**[!UICONTROL Start date]**&#x200B;和&#x200B;**[!UICONTROL End date]**&#x200B;欄位中指定要考慮的刪除期間。 這些日期將包含在期間中。

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >元素刪除期間必須符合CRM的特定限制。 例如，對於Salesforce.com，這表示在30天前刪除的元素無法復原。

## 刪除CRM {#deleting-objects-in-the-crm}中的對象

要刪除CRM端的對象，需要指定要刪除的遠程元素的主鍵。

![](assets/crm_delete_in_crm.png)

**[!UICONTROL Behavior]**&#x200B;標籤可讓您啟用拒絕的處理。 此選項為&#x200B;**[!UICONTROL CRM connector]**&#x200B;活動生成第二個輸出轉變。 有關詳細資訊，請參閱[錯誤處理](#error-processing)。

>[!NOTE]
>
>即使&#x200B;**[!UICONTROL Process rejects]**&#x200B;選項被禁用，也會為每個已拒絕列生成警告。

