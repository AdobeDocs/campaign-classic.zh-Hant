---
product: campaign
title: 存取行銷活動
description: 存取行銷活動
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 2%

---

# 存取行銷活動{#accessing-marketing-campaigns}

![](../../assets/common.svg)

Adobe Campaign允許您建立、配置、執行和分析市場營銷活動。 所有行銷活動都可從統一的控制中心進行管理。 

## 工作區基礎知識 {#workspace-basics}

### 首頁 {#home-page}

連接到Adobe Campaign後，您將看到首頁。

![](assets/campaign_global_view.png)

按一下導航欄中的連結以訪問各種功能。

在 **[!UICONTROL Campaigns]** 頁籤：在這裡，您可以看到市場營銷計畫和市場活動及其子集的概覽。 市場營銷方案由市場活動組成，市場活動由交付、任務、連結資源等組成。 在使用市場活動進行市場營銷市場活動管理的上下文中，有關交付、預算、審閱者和連結文檔的資訊可在市場活動中找到。

的 **[!UICONTROL Browsing]** 塊 **[!UICONTROL Campaigns]** 頁籤提供各種條目，具體取決於實例上安裝的模組。 例如，您可以訪問：

* **市場活動日曆**:計畫日曆、市場營銷計畫、交貨和市場活動。 請參閱 [市場活動日曆](#campaign-calendar)。
* **市場活動**:訪問所有市場營銷計畫中包含的市場活動。
* **交貨**:訪問連結到市場活動的交貨。
* **Web應用程式**:訪問web應用程式（表單、登錄頁等）。

>[!NOTE]
>
>有關Adobe Campaign整體工效學、權限和簡檔管理功能的詳細資訊，請參閱 [此部分](../../platform/using/adobe-campaign-workspace.md)。
>
>與頻道和遞送相關的所有功能均詳見 [此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

### 市場活動日曆 {#campaign-calendar}

每個活動都屬於一個方案，而該方案又屬於一個計畫。 計畫、方案和市場活動可通過 **[!UICONTROL Campaign calendar]** 的 **市場活動** 頁籤。

要編輯計畫、方案、市場活動或交付，請在日曆中按一下其名稱，然後按一下 **[!UICONTROL Open...]**。 然後，它將顯示在新頁籤中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以過濾市場活動日曆中顯示的資訊。 要執行此操作，請按一下 **[!UICONTROL Filter]** 連結並選擇篩選條件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>在日期篩選時，所有起始日期遲於指定日期和/或終止日期早於指定日期的市場活動都會顯示。 需要使用每個欄位右側的日曆選擇日期。

您還可以使用 **[!UICONTROL Search]** 欄位以篩選顯示的項。

連結到每個項目的表徵圖允許您查看其狀態：已完成、正在進行、正在編輯等。

### 瀏覽營銷計畫 {#browsing-in-a-marketing-program}

市場活動允許您管理由各種市場營銷活動組成的一組計畫。 每個市場活動都包含交貨以及關聯的流程和資源。

#### 瀏覽程式 {#browsing-a-program}

編輯程式時，使用下面介紹的頁籤瀏覽和配置程式。

* 的 **計畫** 頁籤根據您在日曆標題中按一下的頁籤顯示月、周或日的程式日曆。

   如有必要，您可以通過此頁建立市場活動、程式或任務。

   ![](assets/s_ncs_user_interface_campaign02.png)

* 的 **編輯** 頁籤，您可以個性化程式：名稱、起始日期和終止日期、預算、連結文檔等。

   ![](assets/s_ncs_user_interface_campaign05.png)

#### 瀏覽市場活動 {#browsing-campaigns}

市場活動可通過市場活動日曆、 **[!UICONTROL Schedule]** 頁籤或市場活動清單。

1. 通過市場活動日曆，選擇要顯示的市場活動，然後按一下 **[!UICONTROL Open]** 的子菜單。

   ![](assets/campaign_planning_edit_op.png)

   市場活動在新標籤中編輯，如下所示：

   ![](assets/campaign_op_edit.png)

1. 通過 **[!UICONTROL Schedule]** 的子菜單。
1. 通過 **[!UICONTROL Campaigns]** 連結 **[!UICONTROL Campaigns]** 頁籤，按一下要編輯的市場活動的名稱。

   ![](assets/campaign_edit_from_list.png)

### 控制市場活動 {#controlling-a-campaign}

#### 儀表板 {#dashboard}

對於每個市場活動，任務、資源和交貨都集中在一個螢幕中 — 控制板，它允許您與其他人協作管理市場營銷活動。

市場活動的控制面板用作控制介面。 它直接訪問主要的市場活動建立和管理階段：交貨、提取檔案、通知、預算等。

![](assets/s_ncs_user_op_board_start_del.png)

通過Adobe Campaign，您可以設定協作流程，以建立和批准營銷和溝通活動的各個階段：預算、目標、內容等的核准

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>市場活動模板的配置在 [市場活動模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

#### 排程 {#schedule}

市場活動集中了一組交貨。 對於每個市場活動，計畫提供所有元件的全局視圖：這樣您就可以顯示任務和交貨，並輕鬆訪問它們。

![](assets/campaign_planning_tab.png)

#### 論壇 {#forum}

對於每次活動，運營商都可以通過專用論壇交換資訊。

有關此內容的詳細資訊，請參閱 [討論論壇](../../mrm/using/discussion-forums.md)。

#### 報告 {#reports}

的 **[!UICONTROL Reports]** 連結允許您訪問市場活動報表。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>報告詳情請參閱 [此部分](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

#### 設定 {#configuration}

市場活動通過市場活動模板建立。 您可以配置可重用模板，其中已為其選擇了某些選項，並且已保存了其他設定。 對於每個市場活動，都提供以下功能：

* 文檔和資源的引用：您可以將文檔與市場活動（簡報、報表、影像等）關聯。 支援所有文檔格式。 請參閱 [管理關聯文檔](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)。
* 定義成本：對於每個市場活動，Adobe Campaign允許您定義成本分錄和成本計算結構，在建立市場營銷市場活動時可以使用這些結構。 例如：印刷成本、使用外部代理、租房等。 請參閱 [定義成本類別](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories)。
* 定義目標：您可以為市場活動定義可量化的目標，例如訂戶數、業務量等。 此資訊稍後將用於市場活動報告。
* 管理種子地址(有關詳細資訊，請參閱 [此部分](../../delivery/using/about-seed-addresses.md))和控制組(請參閱 [定義控制組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group))。
* 管理批准：您可以選擇要批准的處理，並根據需要選擇審閱運算子或運算子組。 請參閱 [檢查和審批交貨](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

>[!NOTE]
>
>要訪問市場活動配置並對其進行更改，請按一下 **[!UICONTROL Advanced campaign parameters...]** 連結 **[!UICONTROL Edit]** 頁籤。

## 使用Web介面 {#using-the-web-interface-}

您可以通過Internet瀏覽器訪問Adobe Campaign控制台螢幕，以查看所有市場活動和交付以及資料庫中配置檔案的報告和資訊。 此訪問不啟用記錄建立。 根據操作員權限，您可以查看和/或對資料庫中的資料執行操作。 例如，您可以批准市場活動內容和目標、重新啟動或停止交付等。

1. 如常登錄：https://`<your instance>:<port>/view/home`。
1. 使用菜單訪問概覽。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

除了在市場活動中導航和查看它們外，您還可以執行以下類型的任務：

* 監視實例上的活動
* 參與驗證流程，例如批准或拒絕交付內容
* 執行其他快速操作，例如暫停工作流
* 訪問所有報告功能
* 參加論壇討論

此表匯總了您可以從瀏覽器對市場活動執行的操作：

| 頁面  | 動作 |
| --- | --- |
| 市場活動、交貨、優惠等清單 | 刪除清單項 |
| Campaign | 取消市場活動 |
| 傳遞 | 批准交付內容和目標<br/>提交交貨內容<br/>確認交貨<br/>暫停和停止交貨 |
| Web應用程式 | 建立Web應用程式<br/>編輯應用程式內容和屬性<br/>將應用程式內容另存為模板<br/>發佈應用程式 |
| 優惠 | 批准聘用內容和資格<br/>禁用線上服務 |
| 任務 | 完成任務<br/>取消任務 |
| 營銷資源 | 審核資源<br/>鎖定和解鎖資源 |
| 市場活動包 | 提交包以供審批<br/>批准或拒絕包<br/>取消包 |
| 市場活動訂單 | 建立訂單<br/>接受或拒絕訂單 <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| 存貨 | 刪除庫存行 |
| 提供模擬 | 啟動和停止模擬 |
| 目標工作流 | 啟動、暫停和停止工作流 |
| 報告 | 在報告歷史記錄中保存當前資料 |
| 論壇 | 添加討論<br/>回復討論中的郵件<br/>關注討論並取消訂閱 |

### 批准

（例如，對目標或傳遞內容）的批准可以通過Web訪問進行。

![](assets/campaign_web_interface_validation.png)

您還可以使用通知消息中包含的連結。 有關此內容的詳細資訊，請參閱 [檢查和審批交貨](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。
