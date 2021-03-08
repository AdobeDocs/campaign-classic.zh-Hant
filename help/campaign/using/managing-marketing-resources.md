---
solution: Campaign Classic
product: campaign
title: 管理行銷資源
description: 管理行銷資源
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 1%

---


# 管理行銷資源{#managing-marketing-resources}

Adobe Campaign可讓您管理和追蹤促銷活動生命週期中涉及的行銷資源。 這些行銷資源可以是手冊、視覺輔助工具或任何其他涉及數位營運商的通訊媒體。

對於透過Adobe Campaign管理的每個行銷資源，您可以隨時追蹤其狀態和歷史記錄並檢視目前版本。

## 新增行銷資源{#adding-a-marketing-resource}

行銷資源可透過&#x200B;**[!UICONTROL Campaigns]**&#x200B;標籤存取。

要添加資源，請按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。

![](assets/s_ncs_user_mkg_resource_add.png)

要使資源在Adobe Campaign伺服器上可用，必須通過將所需資源拖放到編輯器的中間區域來添加該資源。 您也可以按一下&#x200B;**[!UICONTROL Upload file to server...]**&#x200B;連結。

![](assets/s_ncs_user_mkg_resource_file.png)

確認訊息可讓您啟動上傳。

上載完成後，資源將添加到可用資源清單中。 Adobe Campaign運營商可以使用。 他們可以（通過&#x200B;**[!UICONTROL Preview]**&#x200B;頁籤）查看檔案、複製以修改檔案，或更新伺服器上的檔案（使用&#x200B;**[!UICONTROL Edit]**&#x200B;頁籤）。

![](assets/s_ncs_user_mkg_resource_extract.png)

按一下&#x200B;**[!UICONTROL General]**&#x200B;頁籤，選擇負責監視、跟蹤和批准此資源的操作員或操作員組。 通過&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結選擇審核者。

* 分配資源的操作員負責跟蹤該資源。
* 核准營運商負責核准行銷資源。 資源驗證流程啟動時，會通知他們。

   如果未選擇審核者，則資源&#x200B;**[!UICONTROL cannot be]**&#x200B;需要批准。

* 如有必要，您也可以指定校對器。

您可以指定資源的（指示性）可用日期。 在此日期之後，它將顯示為&#x200B;**[!UICONTROL Late]**&#x200B;狀態。

## 資源協作工作{#collaborative-work-on-resources}

您可以修改和更新行銷資源，並視需要通知其他Adobe Campaign營運商。 您可以：

* 在本機下載資源，以進行修改。
* 更新伺服器上的檔案，讓其他營運商也能存取。
* 鎖定資源以禁止其他操作員修改。

>[!NOTE]
>
>**[!UICONTROL History]**&#x200B;頁籤包含資源的下載和更新日誌。 **[!UICONTROL Details]**&#x200B;按鈕可讓您檢視選取的版本：

### 鎖定／解鎖資源{#locking-unlocking-a-resource}

建立後，資源便可在行銷資源控制面板中使用，而營運商可以編輯和修改這些資源。

當操作者希望處理資源時，最好在開始工作之前將其鎖定，以防止其他操作者同時修改資源。 然後保留資源；它仍可存取，但無法由其他運算子在伺服器上發佈或更新。

特殊訊息會通知任何嘗試存取此資訊的營運商：

![](assets/s_ncs_user_mkg_resource_locked.png)

**[!UICONTROL Tracking]**&#x200B;頁籤指示鎖定資源的運算子的名稱和計畫的更新日期。

![](assets/s_ncs_user_mkg_resource_locked_date.png)

要鎖定資源，必須按一下資源儀表板中&#x200B;**[!UICONTROL Lock]**&#x200B;按鈕後面的資源。

![](assets/s_ncs_user_mkg_resource_lock.png)

您可以在資源的&#x200B;**[!UICONTROL Tracking]**&#x200B;標籤中指明計畫退貨日期。

![](assets/s_ncs_user_mkg_resource_lock_date.png)

此資訊可讓您通知其他Adobe Campaign營運商資源解除鎖定的日期。

資源更新後，會自動解除鎖定，並讓所有運算子再次使用。

如有必要，您也可以從控制面板手動解除鎖定。

>[!NOTE]
>
>只有鎖定資源的操作員和具有管理員權限的操作員才有權解鎖資源。

### 論壇 {#discussion-forums}

對於每個資源， **[!UICONTROL Forum]**&#x200B;頁籤允許參與者交換資訊。

[論壇](../../campaign/using/discussion-forums.md) 闡述了論壇在Adobe Campaign的運作方式。

## 行銷資源的生命週期{#life-cycle-of-a-marketing-resource}

建立資源時，將指定Adobe Campaign操作員來設計、校對、批准和發佈資源。 這些促銷活動可以決定持續時間。

**[!UICONTROL Tracking]**&#x200B;頁籤允許您監視資源上執行的任何操作：核准、核准拒絕、相關意見或出版物。

**[!UICONTROL History]**&#x200B;頁籤顯示為此資源執行的檔案傳輸。

### 核准程式{#approval-process}

如果在&#x200B;**[!UICONTROL Tracking]**&#x200B;頁籤中指定了預期可用日期，則該日期將顯示在資源詳細資訊中。 到達此日期後，您可以使用資源儀表板中的&#x200B;**[!UICONTROL Submit for approval]**&#x200B;按鈕執行批准流程。 資源狀態隨後變為&#x200B;**[!UICONTROL Approval in progress]**。

資源可通過其儀表板上的&#x200B;**[!UICONTROL Approve resource]**&#x200B;按鈕獲得批准。

![](assets/s_ncs_user_task_valid_date.png)

然後授權的營運商可以接受或拒絕核准。 您也可以執行下列動作：透過傳送的電子郵件訊息（按一下通知訊息中的連結）或透過主控台（按一下&#x200B;**[!UICONTROL Approve]**）按鈕傳送。

審批窗口可讓您輸入評論。

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

**[!UICONTROL Tracking]**&#x200B;標籤可讓所有運算子追蹤核准程式的不同階段。

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>除了為每個行銷資源指定的審閱者外，具有管理員權限的操作員和資源管理員還被授權批准行銷資源。

### 發佈資源{#publishing-a-resource}

核准後，必須發佈行銷資源。 出版程式必鬚根據公司要求具體實施。 這表示資源可以發佈在外部網站或任何其他伺服器上，特定資訊可以傳送給外部服務供應商等。

若要發佈資源，請按一下行銷資源控制面板編輯區域中的&#x200B;**[!UICONTROL Publish]**&#x200B;按鈕。

![](assets/s_ncs_user_mkg_resource_available.png)

您也可以透過工作流程自動發佈資源。

發佈資源意味著（例如，由其他任務）可供使用。 出版物會因資源性質而異：對於傳單，發佈可能意味著將檔案傳送至印表機、對於網路代理商，也可能意味著將檔案發佈至網站等。

為了讓Adobe Campaign發佈，您需要建立適當的工作流程，並將它連結至資源。 要執行此操作，請開啟資源的&#x200B;**[!UICONTROL Advanced settings]**&#x200B;框，然後在&#x200B;**[!UICONTROL Post-processing]**&#x200B;欄位中選擇所需的工作流。

![](assets/mrm_asset_postprocessing_workflow.png)

將執行工作流：

* 當審核者按一下&#x200B;**[!UICONTROL Publish resource]**&#x200B;連結時（或者，如果未定義審核者，則是資源負責人）。
* 如果資源通過營銷資源建立任務進行管理，則只要在任務中選中&#x200B;**[!UICONTROL Publish the marketing resource]**&#x200B;框，該資源將在任務設定為&#x200B;**[!UICONTROL Finished]**&#x200B;時執行（請參閱[營銷資源建立任務](../../campaign/using/creating-and-managing-tasks.md#marketing-resource-creation-task)）

如果工作流未立即啟動（例如，工作流已停止），則資源的狀態將更改為&#x200B;**[!UICONTROL Pending publication]**。 工作流啟動後，資源的狀態將更改為&#x200B;**[!UICONTROL Published]**。 此狀態未考慮發佈程式中可能發生的錯誤。 檢查工作流程的狀態，以確認其已正確執行。

## 將資源連結至促銷活動{#linking-a-resource-to-a-campaign}

### 參考行銷資源{#referencing-a-marketing-resource}

行銷資源可與促銷活動相關聯，前提是促銷活動範本中已選取此功能。

>[!NOTE]
>
>如需如何建立和設定促銷活動範本的詳細資訊，請參閱[促銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

按一下促銷活動控制面板中的&#x200B;**[!UICONTROL Documents > Resources]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選取相關的資源。

![](assets/s_ncs_user_mkg_resource_ref.png)

您可以依狀態、性質或類型來篩選資源，或套用個人化篩選。

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

按一下&#x200B;**[!UICONTROL OK]**，將資源新增至此促銷活動參考的行銷資源清單。

**[!UICONTROL Details]**&#x200B;按鈕可讓您編輯和檢視它。

新增的資源會顯示在控制面板中。 您也可以在此編輯。

### 將行銷資源新增至傳送大綱{#adding-a-marketing-resource-to-a-delivery-outline}

行銷資源可透過傳送大綱與傳送相關聯。

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>有關交付大綱的詳細資訊，請參閱[關聯和構建通過交付大綱連結的資源](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

## 股票管理{#stock-management}

您可以將行銷資源與一個或多個庫存關聯，以便管理您的供應，並在庫存不足時在控制面板上顯示警告。

>[!NOTE]
>
>有關Adobe Campaign的股票管理詳情，請參閱[股票管理](../../campaign/using/providers--stocks-and-budgets.md#stock-management)。

若要將行銷資源與庫存建立關聯，請編輯庫存對應並編輯或建立庫存。 新增庫存行並選取對應的行銷資源。

![](assets/s_ncs_user_task_in_a_stock.png)

如有必要，您可以在選取資源後，透過資源右側的&#x200B;**[!UICONTROL Edit the link]**&#x200B;圖示（放大鏡）編輯選取的資源。

指定初始庫存和警報庫存，然後儲存。

庫存在資源詳細資訊中。

![](assets/s_ncs_user_task_with_a_stock.png)

當庫存不足時，會向相關營運商發出警告。

## 進階函式 {#advanced-functions}

行銷資源控制面板可讓您執行常見的作業類型：新增、編輯、鎖定／解除鎖定、核准、發佈。 您可以建立其他類型的行銷資源，並透過Adobe Campaign樹狀結構存取進階功能。 要執行此操作，請按一下Adobe Campaign首頁中的&#x200B;**[!UICONTROL Explorer]**。

預設情況下，行銷資源儲存在樹的&#x200B;**[!UICONTROL MRM > Marketing resources]**&#x200B;節點中。

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

您可以從此視圖添加以下資源：

* 檔案
* HTML
* 文字
* URL

