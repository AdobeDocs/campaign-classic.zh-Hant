---
product: campaign
title: 存取行銷活動
description: 存取行銷活動
role: User
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 2%

---

# 存取行銷活動{#accessing-marketing-campaigns}

Adobe Campaign可讓您建立、設定、執行和分析行銷活動。 所有行銷活動都可從統一的控制中心進行管理。

## 工作區基本知識 {#workspace-basics}

### 首頁 {#home-page}

連線至Adobe Campaign後，請使用導覽列中的連結來瀏覽各種功能。


![](assets/campaign_global_view.png)


行銷活動元素位於 **[!UICONTROL Campaigns]** 標籤：您可以在此處檢視行銷方案、行銷活動及其子集的概觀。 行銷方案由行銷活動組成，行銷活動由傳遞、任務、連結資源等組成。 在使用Campaign進行行銷活動管理的情況下，傳送、預算、稽核者和連結檔案的相關資訊可在行銷活動中找到。

此 **[!UICONTROL Browsing]** 區塊 **[!UICONTROL Campaigns]** 索引標籤會根據執行個體上安裝的模組，提供各種專案。 例如，您可以存取：

* **行銷活動行事曆**：計畫、行銷方案、傳遞和行銷活動的行事曆。 請參閱 [行銷活動行事曆](#campaign-calendar).
* **行銷活動**：存取所有行銷方案中所包含的促銷活動。
* **傳遞**：存取連結至行銷活動的傳送。
* **網頁應用程式**：存取網路應用程式（表單、登陸頁面等）。

>[!NOTE]
>
>如需整體Adobe Campaign人體工學、許可權和設定檔管理功能的詳細資訊，請參閱 [本節](../../platform/using/adobe-campaign-workspace.md).
>
>與管道和傳送相關的所有功能都詳見 [本節](../../delivery/using/steps-about-delivery-creation-steps.md).

### 行銷活動行事曆 {#campaign-calendar}

每個行銷活動都屬於一個方案，而該方案又屬於一個計畫。 計畫、方案和行銷活動可透過以下方式存取： **[!UICONTROL Campaign calendar]** 功能表 **行銷活動** 標籤。

若要編輯計畫、方案、行銷活動或傳遞，請在行事曆中按一下其名稱，然後按一下 **[!UICONTROL Open...]**. 然後它會顯示在新的標籤中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以篩選行銷活動行事曆中顯示的資訊：按一下 **[!UICONTROL Filter]** 連結並選取篩選條件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>依日期篩選時，會顯示開始日期晚於指定日期及/或結束日期早於指定日期的所有行銷活動。 使用每個欄位右側的行事曆選取日期。

您也可以使用 **[!UICONTROL Search]** 欄位以篩選顯示的專案。

連結至每個專案的圖示可讓您檢視其狀態：已完成、進行中、正在編輯等。

### 瀏覽行銷方案 {#browsing-in-a-marketing-program}

Campaign可讓您管理一組方案，由各種行銷活動組成。 每個行銷活動包含傳遞及關聯的流程和資源。

#### 瀏覽程式 {#browsing-a-program}

編輯程式時，請使用下述標籤來瀏覽及設定程式。

* 此 **排程** 索引標籤會根據您在日曆標題中按一下哪個索引標籤，顯示某個月、周或天的方案行事曆。

  如有必要，您可以透過此頁面建立行銷活動、方案或任務。

  ![](assets/s_ncs_user_interface_campaign02.png)

* 此 **編輯** 索引標籤可讓您個人化方案：名稱、開始和結束日期、預算、連結檔案等。

  ![](assets/s_ncs_user_interface_campaign05.png)

#### 瀏覽行銷活動 {#browsing-campaigns}

行銷活動可透過行銷活動行事曆 **[!UICONTROL Schedule]** 方案索引標籤或行銷活動清單。

1. 透過行銷活動行事曆，選取您要顯示的行銷活動，然後按一下 **[!UICONTROL Open]** 連結。

   ![](assets/campaign_planning_edit_op.png)

   行銷活動會在新標籤中編輯，如下所示：

   ![](assets/campaign_op_edit.png)

1. 透過 **[!UICONTROL Schedule]** 索引標籤中，編輯模式與透過行銷活動行事曆傳送的相同。
1. 透過 **[!UICONTROL Campaigns]** 的連結 **[!UICONTROL Campaigns]** 索引標籤上，按一下您要編輯的行銷活動名稱。

   ![](assets/campaign_edit_from_list.png)

### 控制行銷活動 {#controlling-a-campaign}

#### 儀表板 {#dashboard}

針對每個行銷活動，工作、資源和傳遞都集中在一個畫面中（控制面板），可讓您協同合作管理行銷動作。

行銷活動的控制面板會作為控制介面。 它直接存取主要行銷活動建立和管理階段：傳送、擷取檔案、通知、預算等。

![](assets/s_ncs_user_op_board_start_del.png)

透過Adobe Campaign，您可以設定合作流程，以建立和核准行銷和通訊行銷活動的各個階段：核准預算、目標、內容等。

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>行銷活動範本的設定顯示於 [行銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### 排程 {#schedule}

行銷活動會集中一組傳遞。 對於每個行銷活動，排程提供所有元件的全域檢視：您可以顯示任務和傳送，並輕鬆存取。

![](assets/campaign_planning_tab.png)

#### 論壇 {#forum}

對於每個行銷活動，操作員可透過專用論壇交換訊息。

進一步瞭解 [論壇](../../mrm/using/discussion-forums.md).

#### 報告 {#reports}

此 **[!UICONTROL Reports]** 連結可讓您存取行銷活動報表。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>報告中詳細說明 [本節](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### 設定 {#configuration}

行銷活動是透過行銷活動範本建立。 您可以設定已選取某些選項且已儲存其他設定的可重複使用範本。 每個行銷活動皆提供下列功能：

* 引用 [檔案和資源](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)：您可以將檔案與行銷活動建立關聯（簡介、報告、影像等）。 支援所有檔案格式。
* 定義成本：Adobe Campaign可讓您針對每個促銷活動定義 [成本輸入與成本計算結構](../../campaign/using/providers-stocks-and-budgets.md#defining-cost-categories) ，可在建立行銷活動時使用。 例如：列印成本、使用外部代理商、房間租金。
* 定義目標：您可以定義行銷活動的可量化目標，例如訂閱者人數、業務量等。 此資訊稍後會用於行銷活動報表。
* 管理 [種子地址](../../delivery/using/about-seed-addresses.md) 和 [控制組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* 管理核准：您可以選取要核准的處理方式，並視需要選取複查操作員或操作員群組。 [了解更多](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>若要存取行銷活動設定並進行變更，請按一下 **[!UICONTROL Advanced campaign parameters...]** 中的連結 **[!UICONTROL Edit]** 標籤。

## 使用網頁介面 {#using-the-web-interface-}

您可以透過網際網路瀏覽器存取Adobe Campaign主控台畫面，以檢視所有行銷活動和傳送，以及資料庫中設定檔的報告和資訊。 此存取權不會啟用記錄建立。 根據操作員的許可權，您可以檢視和/或操作資料庫中的資料。 例如，您可以核准行銷活動內容和目標定位、重新啟動或停止傳送等。

1. 照常透過https://登入`<your instance>:<port>/view/home`.
1. 使用功能表存取概述。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

除了導覽和檢視行銷活動之外，您還可以執行下列型別的工作：

* 監視執行個體上的活動
* 參與驗證程式，例如，核准或拒絕傳遞內容
* 執行其他快速動作，例如暫停工作流程
* 存取所有報告功能
* 參與論壇討論

此表格總結列出您可從瀏覽器對行銷活動採取的動作：

| 頁面  | 動作 |
| --- | --- |
| 行銷活動、傳遞、優惠方案等清單。 | 刪除清單專案 |
| Campaign | 取消行銷活動 |
| 傳遞 | 核准傳遞內容和目標<br/>提交傳遞內容<br/>確認傳遞<br/>暫停和停止傳遞 |
| 網頁應用程式 | 建立網站應用程式<br/>編輯應用程式內容和屬性<br/>將應用程式內容另存為範本<br/>發佈應用程式 |
| 優惠 | 核准優惠方案內容和資格<br/>停用線上選件 |
| 任務 | 完成任務<br/>取消任務 |
| 行銷資源 | 核准資源<br/>鎖定及解除鎖定資源 |
| 行銷活動套件 | 提交套件以供核准<br/>核准或拒絕套件<br/>取消套裝 |
| 行銷活動訂單 | 建立訂單<br/>接受或拒絕訂單 <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| 庫存 | 刪除庫存行 |
| 優惠方案模擬 | 開始和停止模擬 |
| 目標定位工作流程 | 開始、暫停和停止工作流程 |
| 報告 | 將目前的資料儲存在報告歷史記錄中 |
| 論壇 | 新增討論<br/>回覆討論中的訊息<br/>關注討論內容並取消訂閱 |

### 核准

（例如，目標或傳遞內容的）核准可透過網頁存取執行。

![](assets/campaign_web_interface_validation.png)

您也可以使用通知訊息中包含的連結。 有關詳細資訊，請參閱 [檢查及核准傳遞](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
