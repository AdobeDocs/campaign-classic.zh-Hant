---
product: campaign
title: 存取行銷活動
description: 存取行銷活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 3%

---

# 存取行銷活動{#accessing-marketing-campaigns}

Adobe Campaign可讓您建立、設定、執行和分析行銷活動。 所有行銷活動都可從統一的控制中心進行管理。 

## 工作區基本介紹 {#workspace-basics}

### 首頁 {#home-page}

連線至Adobe Campaign後，使用導覽列中的連結來瀏覽各種功能。


![](assets/campaign_global_view.png)


在 **[!UICONTROL Campaigns]** 標籤：您可以在此查看行銷方案、行銷活動及其子集的概觀。 行銷方案由行銷活動組成，行銷活動由傳遞、工作、連結資源等組成。 在使用Campaign進行行銷活動管理的情境中，有關傳送、預算、審閱者和連結檔案的資訊可在行銷活動中找到。

此 **[!UICONTROL Browsing]** 區塊 **[!UICONTROL Campaigns]** 索引標籤會根據執行個體上安裝的模組提供各種項目。 例如，您可以存取：

* **行銷活動日曆**:計畫、行銷方案、傳遞和行銷活動行事歷。 請參閱 [行銷活動日曆](#campaign-calendar).
* **行銷活動**:存取所有行銷方案中包含的行銷活動。
* **傳遞**:存取連結至促銷活動的傳送。
* **Web應用程式**:存取網頁應用程式（表單、登錄頁面等）。

>[!NOTE]
>
>有關整體Adobe Campaign人機工程學、權限和設定檔管理功能的詳細資訊，請參閱 [本節](../../platform/using/adobe-campaign-workspace.md).
>
>有關管道和傳遞的所有功能，請參閱 [本節](../../delivery/using/steps-about-delivery-creation-steps.md).

### 行銷活動日曆 {#campaign-calendar}

每個促銷活動都屬於一個方案，而該方案又屬於一個計畫。 計畫、方案和促銷活動可透過 **[!UICONTROL Campaign calendar]** 功能表 **行銷活動** 標籤。

若要編輯計畫、方案、行銷活動或傳送，請在日曆中按一下其名稱，然後按一下 **[!UICONTROL Open...]**. 接著會顯示在新標籤中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以篩選行銷活動日曆中顯示的資訊：按一下 **[!UICONTROL Filter]** 連結，然後選取篩選條件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>當您依日期篩選時，會顯示所有開始日期晚於指定日期和/或結束日期早於指定日期的促銷活動。 使用每個欄位右側的日曆選擇日期。

您也可以使用 **[!UICONTROL Search]** 欄位來篩選顯示的項目。

連結至每個項目的圖示可讓您檢視其狀態：已完成、進行中、正在編輯等。

### 在行銷方案中瀏覽 {#browsing-in-a-marketing-program}

Campaign可讓您管理由各種行銷活動組成的一組方案。 每個促銷活動都包含傳遞以及相關的程式和資源。

#### 瀏覽程式 {#browsing-a-program}

編輯程式時，請使用下面描述的頁簽來瀏覽和配置它。

* 此 **排程** 頁簽顯示月、周或日的方案日曆，具體取決於您在日曆頁首中按一下的頁簽。

   如有必要，您可以透過此頁面建立促銷活動、方案或任務。

   ![](assets/s_ncs_user_interface_campaign02.png)

* 此 **編輯** 標籤可讓您個人化方案：名稱、開始和結束日期、預算、連結的檔案等。

   ![](assets/s_ncs_user_interface_campaign05.png)

#### 瀏覽促銷活動 {#browsing-campaigns}

您可透過促銷活動行事歷， **[!UICONTROL Schedule]** 方案的索引標籤，或行銷活動清單。

1. 透過促銷活動日曆，選取您要顯示的促銷活動，然後按一下 **[!UICONTROL Open]** 連結。

   ![](assets/campaign_planning_edit_op.png)

   促銷活動會在新索引標籤中編輯，如下所示：

   ![](assets/campaign_op_edit.png)

1. 透過 **[!UICONTROL Schedule]** 方案的索引標籤中，編輯模式與透過促銷活動日曆的相同。
1. 透過 **[!UICONTROL Campaigns]** 連結 **[!UICONTROL Campaigns]** 標籤，按一下您要編輯的促銷活動名稱。

   ![](assets/campaign_edit_from_list.png)

### 控制行銷活動 {#controlling-a-campaign}

#### 儀表板 {#dashboard}

對於每個促銷活動，工作、資源和傳送會集中在單一畫面（即控制面板）中，讓您與其他人共同管理行銷動作。

促銷活動的控制面板是作為控制介面使用。 它直接存取主要促銷活動建立和管理階段：傳遞、擷取檔案、通知、預算等。

![](assets/s_ncs_user_op_board_start_del.png)

透過Adobe Campaign，您可以設定協作流程，以建立和核准行銷和通訊行銷活動的各個階段：預算、目標、內容等的核准。

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>行銷活動範本的設定顯示在 [行銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### 排程 {#schedule}

促銷活動會集中一組傳送。 對於每個促銷活動，排程會提供所有元件的全域檢視：您可以顯示工作和傳送，並輕鬆存取。

![](assets/campaign_planning_tab.png)

#### 論壇 {#forum}

對於每個促銷活動，操作者可透過專用論壇交換訊息。

深入了解 [論壇](../../mrm/using/discussion-forums.md).

#### 報告 {#reports}

此 **[!UICONTROL Reports]** 連結可讓您存取促銷活動報表。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>報表在 [本節](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### 設定 {#configuration}

行銷活動是透過行銷活動範本建立。 您可以配置可重複使用的模板，其中已為其選擇了某些選項，並且已保存了其他設定。 對於每個促銷活動，提供下列功能：

* 引用 [檔案和資源](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents):您可以將檔案與促銷活動（簡報、報表、影像等）建立關聯。 支援所有文檔格式。
* 定義成本：針對每個促銷活動，Adobe Campaign可讓您 [成本條目和成本計算結構](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories) 可用於建立行銷活動。 例如：印刷費用，使用外部代理，房間租賃。
* 定義目標：您可以為促銷活動定義可量化的目標，例如訂閱者數量、業務量等。 此資訊稍後會用於行銷活動報表。
* 管理 [種子地址](../../delivery/using/about-seed-addresses.md) 和 [控制組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* 管理核准：您可以選取要核准的處理，並視需要選取檢閱運算子或運算子群組。 [了解更多](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>若要存取促銷活動設定並進行變更，請按一下 **[!UICONTROL Advanced campaign parameters...]** 連結 **[!UICONTROL Edit]** 標籤。

## 使用Web介面 {#using-the-web-interface-}

您可以透過網際網路瀏覽器存取Adobe Campaign主控台畫面，以檢視所有促銷活動和傳送，以及資料庫中設定檔的報表和資訊。 此訪問不啟用記錄建立。 根據操作員權限，您可以查看和/或對資料庫中的資料執行操作。 例如，您可以核准促銷活動內容及鎖定目標、重新啟動或停止傳送等。

1. 照常透過https://登入`<your instance>:<port>/view/home`.
1. 使用功能表存取概述。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

除了瀏覽各個促銷活動並檢視它們，您還可以執行下列類型的工作：

* 監視執行個體上的活動
* 參與驗證程式，例如核准或拒絕傳送內容
* 執行其他快速動作，例如暫停工作流程
* 存取所有報表功能
* 參加論壇討論

此表格會摘要您可從瀏覽器對促銷活動採取的動作：

| 頁面  | 動作 |
| --- | --- |
| 促銷活動、傳送、選件等的清單。 | 刪除清單項目 |
| Campaign | 取消促銷活動 |
| 傳遞 | 核准傳遞內容和目標<br/>提交傳遞內容<br/>確認傳送<br/>暫停並停止傳送 |
| 網頁應用程式 | 建立Web應用程式<br/>編輯應用程式內容和屬性<br/>將應用程式內容另存為模板<br/>發佈應用程式 |
| 優惠 | 核准優惠方案內容和資格<br/>停用線上優惠方案 |
| 任務 | 完成任務<br/>取消任務 |
| 行銷資源 | 核准資源<br/>鎖定和解除鎖定資源 |
| 行銷活動套件 | 提交套件以進行核准<br/>批准或拒絕包<br/>取消包 |
| 行銷活動訂單 | 建立訂單<br/>接受或拒絕訂單 <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| 庫存 | 刪除庫存行 |
| 優惠方案模擬 | 啟動和停止模擬 |
| 目標工作流程 | 啟動、暫停和停止工作流程 |
| 報告 | 在報表歷史記錄中儲存目前的資料 |
| 論壇 | 添加討論<br/>回復討論中的郵件<br/>按照討論結果取消訂閱 |

### 核准

核准（例如目標或傳送內容）可透過Web存取執行。

![](assets/campaign_web_interface_validation.png)

您也可以使用通知訊息中包含的連結。 有關詳細資訊，請參閱 [檢查和核准傳遞](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
