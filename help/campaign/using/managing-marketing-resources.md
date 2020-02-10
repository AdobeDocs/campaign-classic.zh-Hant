---
title: 管理行銷資源
seo-title: 管理行銷資源
description: 管理行銷資源
seo-description: null
page-status-flag: never-activated
uuid: 35333bcb-0749-45b1-98ab-d5de6d91861c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 069dbc6b-4019-4d66-85a8-0e4de6b66f18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e09692e316a92a67632201e5691e8b4df42cc341

---


# 管理行銷資源{#managing-marketing-resources}

Adobe Campaign可讓您管理和追蹤促銷活動生命週期中涉及的行銷資源。 這些行銷資源可以是手冊、視覺輔助工具或任何其他涉及數位營運商的通訊媒體。

對於透過Adobe Campaign管理的每個行銷資源，您可以隨時追蹤其狀態和歷史記錄，並檢視目前的版本。

## 新增行銷資源 {#adding-a-marketing-resource}

行銷資源可透過「行銷活動」範圍存取。

要添加資源，請按一下該 **[!UICONTROL Create]** 按鈕。

![](assets/s_ncs_user_mkg_resource_add.png)

若要讓資源可在Adobe Campaign伺服器上使用，您必須將所需資源拖放至編輯器的中間區域，以新增它。 您也可以按一下連 **[!UICONTROL Upload file to server...]** 結。

![](assets/s_ncs_user_mkg_resource_file.png)

確認訊息可讓您啟動上傳。

上載完成後，資源將添加到可用資源清單中。 Adobe Campaign營運商可存取它。 他們可以（透過標籤）檢 **[!UICONTROL Preview]****[!UICONTROL Edit]** 視檔案、製作要修改的復本，或在伺服器上更新檔案（使用標籤）。

![](assets/s_ncs_user_mkg_resource_extract.png)

按一下該 **[!UICONTROL General]** 頁籤以選擇負責監視、跟蹤和批准此資源的操作員或操作員組。 選擇審閱者是通過連結完 **[!UICONTROL Advanced parameters]** 成的。

* 分配資源的操作員負責跟蹤該資源。
* 核准營運商負責核准行銷資源。 資源驗證流程啟動時，會通知他們。

   如果未選擇審核者，則需要 **[!UICONTROL cannot be]** 批准資源。

* 如有必要，您也可以指定校對器。

您可以指定資源的（指示性）可用日期。 在此日期之後，它會以狀態顯 **[!UICONTROL Late]** 示。

## 資源協作工作 {#collaborative-work-on-resources}

您可以修改和更新行銷資源，並視需要通知其他Adobe Campaign營運商。 您可以：

* 在本機下載資源，以進行修改。
* 更新伺服器上的檔案，讓其他營運商也能存取。
* 鎖定資源以禁止其他操作員修改。

>[!NOTE]
>
>該選 **[!UICONTROL History]** 項卡包含資源的下載和更新日誌。 此按 **[!UICONTROL Details]** 鈕可讓您檢視選取的版本：

### 鎖定／解鎖資源 {#locking-unlocking-a-resource}

建立後，資源便可在行銷資源控制面板中使用，而營運商可以編輯和修改這些資源。

當操作者希望處理資源時，最好在開始工作之前將其鎖定，以防止其他操作者同時修改資源。 然後保留資源；它仍可存取，但無法由其他運算子在伺服器上發佈或更新。

特殊訊息會通知任何嘗試存取此資訊的營運商：

![](assets/s_ncs_user_mkg_resource_locked.png)

此標 **[!UICONTROL Tracking]** 簽指明鎖定資源的操作員的名稱和計畫的更新日期。

![](assets/s_ncs_user_mkg_resource_locked_date.png)

要鎖定資源，必須按一下資源儀表板中的 **[!UICONTROL Lock]** 按鈕後面的資源。

![](assets/s_ncs_user_mkg_resource_lock.png)

您可以在資源的標籤中指明 **[!UICONTROL Tracking]** 計畫退貨日期。

![](assets/s_ncs_user_mkg_resource_lock_date.png)

這項資訊可讓您通知其他Adobe Campaign營運商資源解除鎖定的日期。

資源更新後，會自動解除鎖定，並讓所有運算子再次使用。

如有必要，您也可以從控制面板手動解除鎖定。

>[!NOTE]
>
>只有鎖定資源的操作員和具有管理員權限的操作員才有權解鎖資源。

### 論壇 {#discussion-forums}

對於每個資源，該選 **[!UICONTROL Forum]** 項卡允許參與者交換資訊。

[論壇說明](../../campaign/using/discussion-forums.md) ，論壇在Adobe Campaign中如何運作。

## 行銷資源的生命週期 {#life-cycle-of-a-marketing-resource}

在建立資源時，會指定Adobe Campaign營運商來設計、校對、核准和發佈資源。 這些促銷活動可以決定持續時間。

該選 **[!UICONTROL Tracking]** 項卡可讓您監視在資源上執行的任何操作：核准、核准拒絕、相關意見或出版物。

該選 **[!UICONTROL History]** 項卡顯示為此資源執行的檔案傳輸。

### 核准程式 {#approval-process}

如果在頁籤中指定了預期可用日期，則資源詳細資訊中將顯示該預期可用 **[!UICONTROL Tracking]** 日期。 到達此日期後，您可以使用資源儀表板中的按鈕 **[!UICONTROL Submit for approval]** 執行批准流程。 然後資源狀態將更改為 **[!UICONTROL Approval in progress]**。

資源可透過其控制面板上 **[!UICONTROL Approve resource]** 的按鈕進行核准。

![](assets/s_ncs_user_task_valid_date.png)

然後授權的營運商可以接受或拒絕核准。 您也可以執行下列動作：透過傳送的電子郵件訊息（按一下通知訊息中的連結）或透過主控台(按一下 **[!UICONTROL Approve]** )按鈕。

審批窗口可讓您輸入評論。

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

此標 **[!UICONTROL Tracking]** 簽可讓所有運算子追蹤核准程式的不同階段。

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>除了為每個行銷資源指定的審閱者外，具有管理員權限的操作員和資源管理員還被授權批准行銷資源。

### 發佈資源 {#publishing-a-resource}

核准後，必須發佈行銷資源。 出版程式必鬚根據公司要求具體實施。 這表示資源可以發佈在外部網站或任何其他伺服器上，特定資訊可以傳送給外部服務供應商等。

若要發佈資源，請按一下行 **[!UICONTROL Publish]** 銷資源控制面板編輯區域中的按鈕。

![](assets/s_ncs_user_mkg_resource_available.png)

您也可以透過工作流程自動發佈資源。

發佈資源意味著（例如，由其他任務）可供使用。 出版物會因資源性質而異：對於傳單，發佈可能意味著將檔案傳送至印表機、對於網路代理商，也可能意味著將檔案發佈至網站等。

為了讓Adobe Campaign發佈，您需要建立適當的工作流程並將其連結至資源。 若要這麼做，請開啟資 **[!UICONTROL Advanced settings]** 源的方塊，然後在欄位中選取所要的工作流程 **[!UICONTROL Post-processing]** 。

![](assets/mrm_asset_postprocessing_workflow.png)

工作流將執行：

* 當審核者按一下鏈 **[!UICONTROL Publish resource]** 接時（或者，如果未定義審核者，則為資源負責人）。
* 如果資源是通過行銷資源建立任務管理的，則只要選定任務中的框 **[!UICONTROL Finished]**，就會在該任務設定為時執行(請參閱 **[!UICONTROL Publish the marketing resource]** Marketing資源建立任務 [](../../campaign/using/creating-and-managing-tasks.md#marketing-resource-creation-task))

如果工作流未立即啟動（例如，如果工作流已停止），則資源的狀態將更改為 **[!UICONTROL Pending publication]**。 啟動工作流後，資源的狀態將更改為 **[!UICONTROL Published]**。 此狀態未考慮發佈程式中的可能錯誤。 檢查工作流程的狀態，以確認其已正確執行。

## 將資源連結至促銷活動 {#linking-a-resource-to-a-campaign}

### 參考行銷資源 {#referencing-a-marketing-resource}

行銷資源可與促銷活動相關聯，前提是促銷活動範本中已選取此功能。

>[!NOTE]
>
>如需如何建立和設定促銷活動範本的詳細資訊，請參閱促銷 [活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

按一下促 **[!UICONTROL Documents > Resources]** 銷活動控制面板中的標籤，然 **[!UICONTROL Add]** 後按一下以選擇相關資源。

![](assets/s_ncs_user_mkg_resource_ref.png)

您可以依狀態、性質或類型來篩選資源，或套用個人化篩選。

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

按一 **[!UICONTROL OK]** 下，將資源新增至此促銷活動參考的行銷資源清單。

按 **[!UICONTROL Details]** 鈕可讓您編輯和檢視。

新增的資源會顯示在控制面板中。 您也可以在此編輯。

### 新增行銷資源至傳送大綱 {#adding-a-marketing-resource-to-a-delivery-outline}

行銷資源可透過傳送大綱與傳送相關聯。

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>有關交付大綱的詳細資訊，請參 [閱關聯和構建通過交付大綱連結的資源](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

## 股票管理 {#stock-management}

您可以將行銷資源與一個或多個庫存關聯，以便管理您的供應，並在庫存不足時在控制面板上顯示警告。

>[!NOTE]
>
>如需Adobe Campaign中庫存管理的詳細資訊，請參閱 [Stock管理](../../campaign/using/providers--stocks-and-budgets.md#stock-management)。

若要將行銷資源與庫存建立關聯，請編輯庫存對應並編輯或建立庫存。 新增庫存行並選取對應的行銷資源。

![](assets/s_ncs_user_task_in_a_stock.png)

如有必要，您可以在選取資源後，透過 **[!UICONTROL Edit the link]** 位於資源右側的圖示（放大鏡）來編輯選取的資源。

指定初始庫存和警報庫存，然後儲存。

庫存在資源詳細資訊中。

![](assets/s_ncs_user_task_with_a_stock.png)

當庫存不足時，會向相關營運商發出警告。

## 進階函式 {#advanced-functions}

行銷資源控制面板可讓您執行常見的作業類型：新增、編輯、鎖定／解除鎖定、核准、發佈。 您可以建立其他類型的行銷資源，並透過Adobe Campaign樹狀結構存取進階功能。 若要這麼做，請按 **[!UICONTROL Explorer]** 一下Adobe Campaign首頁中的。

依預設，行銷資源會儲存在樹 **[!UICONTROL MRM > Marketing resources]** 狀結構的節點中。

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

您可以從此視圖添加以下資源：

* 檔案
* HTML
* 文字
* URL

