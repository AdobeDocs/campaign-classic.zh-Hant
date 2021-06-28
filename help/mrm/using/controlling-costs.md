---
product: campaign
title: 控制成本
description: 了解如何控製成本
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 6765e307-915a-44d2-a486-85c64e8ec52e
source-git-commit: 690f7c4e62203127da7a7055afa0ee8ad4a2bce4
workflow-type: tm+mt
source-wordcount: '2468'
ht-degree: 0%

---

# 控制成本{#controlling-costs}

Adobe Campaign可讓您控制已排程、已提交和已開票的行銷成本，並使用「行銷資源管理」模組依類別加以劃分。

行銷部門預先定義的預算中，會計入行銷活動各個流程的承諾成本。 這些金額可細分為數個類別，讓資訊更容易閱讀，並提供行銷投資的更詳細報告。

預算的管理與追蹤會集中在Adobe Campaign樹狀結構的專用節點中。 這可讓您監控來自相同檢視和所有預算的已分配、保留、已承諾和花費金額。

![](assets/s_ncs_user_budget_node_02.png)

使用MRM實施預算管理必須套用下列步驟：

1. 定義預算

   有關詳細資訊，請參閱[建立預算](#creating-a-budget)。

1. 定義成本計算方法

   為服務提供商定義成本結構。 請參閱[建立服務提供商及其成本類別](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

1. 定義促銷活動成本（傳遞/任務）

   傳遞和任務產生的成本會單獨或全域輸入行銷活動範本。 請參閱[成本和庫存計算](../../campaign/using/marketing-campaign-deliveries.md#calculation-of-costs-and-stocks)。

1. 整合

   根據任務、交付和促銷活動的進度狀態，將計算成本並傳遞至相應的預算。

   當建立促銷活動足夠進階時，促銷活動預算的進度狀態可變更為&#x200B;**[!UICONTROL Specified]**。 然後，將自動輸入方案的計算成本，以及在促銷活動上計算的成本。 請參閱[成本承諾、計算和費用](#cost-commitment--calculation-and-charging)。

## 建立預算 {#creating-a-budget}

預算是透過&#x200B;**[!UICONTROL Campaign management > Budgets]**&#x200B;節點在地圖中建立。 工具列中的&#x200B;**[!UICONTROL New]**&#x200B;按鈕可讓您建立預算。

* 新增預算

   按一下&#x200B;**[!UICONTROL New]**&#x200B;圖示，命名並儲存預算。

* 輸入初始金額

   在相關欄位中指定分配的金額。 系統會自動輸入其他金額。 請參閱[計算金額](#calculating-amounts)。

* 定義有效期

   指定開始和結束日期。 此資訊僅表示性。

* 費用

   建立為促銷活動、任務等分配給此預算的成本的支出類別。 可以連結。 請參閱[費用類別](#expense-categories)。

   ![](assets/s_ncs_user_budget_create_and_save.png)

>[!NOTE]
>
>您可以選取相關預算。
>
>有關詳細資訊，請參閱[將預算連結到另一個](#linking-a-budget-to-another)。

### 計算金額 {#calculating-amounts}

每個預算都由初始金額定義，該金額將在計畫或執行促銷活動、傳送或與其相關的任務的成本中減少。 金額的狀態（計畫、保留、承諾、花費或開票）取決於成本類型和在促銷活動、交付或任務中定義的承諾級別。

>[!NOTE]
>
>為類別輸入的金額必須與&#x200B;**[!UICONTROL Allocated]**&#x200B;欄位中定義的預算信封相匹配。

對於行銷活動，可根據承諾程度來規劃、承諾或預留成本，以供未來行動使用。

![](assets/s_user_cost_op_engaged.png)

>[!CAUTION]
>
>建立促銷活動時，**[!UICONTROL Budget]**&#x200B;中的進度狀態必須設為&#x200B;**[!UICONTROL Defined]**，才能在執行時考慮成本。 如果狀態為&#x200B;**[!UICONTROL Being edited]**，則不會合併成本。
>   
>選項&#x200B;**[!UICONTROL Commitment level]**&#x200B;代表在將費用列入預算之前對未來費用的預測。 根據促銷活動、任務或傳送的進度，您可以決定指派較高或較低的承諾等級(1)。 計畫2。 保留，3。 已提交)。

例如，網路促銷活動的預計計畫成本為45,000歐元。

![](assets/s_user_edit_budget_node_impact_0.png)

對於促銷活動，當預算建立狀態設為&#x200B;**[!UICONTROL Defined]**&#x200B;時，促銷活動的實際成本（或如果沒有，則計算成本）將轉入預算總計中。

![](assets/s_user_budget_in_op_a.png)

根據促銷活動預算的承諾量，金額將輸入&#x200B;**[!UICONTROL Planned]**、**[!UICONTROL Reserved]**&#x200B;或&#x200B;**[!UICONTROL Committed]**&#x200B;欄位中。

承諾級別可以修改：

* 在&#x200B;**campaign**&#x200B;層級的&#x200B;**[!UICONTROL Budget]**&#x200B;視窗中，在&#x200B;**[!UICONTROL Edit]**&#x200B;標籤中找到。 這是配置預算、成本和費用的地方。
* 在&#x200B;**tasks**&#x200B;級別的&#x200B;**[!UICONTROL Expenses and revenues]**&#x200B;窗口中。

![](assets/s_user_op_engagement_level_costs.png)

當預算為&#x200B;**[!UICONTROL Reserved]**&#x200B;時，將自動為已計費預算執行更新。

![](assets/s_user_edit_budget_node_impact_2.png)

在任務級別上，該過程相同。

![](assets/s_user_edit_budget_node_impact_task.png)

當支出產生髮票並支付發票時，其金額隨後輸入&#x200B;**[!UICONTROL Invoiced]**&#x200B;欄位。

### 費用類別 {#expense-categories}

這些金額可以分散在數個費用類別中，以便更容易閱讀資料，並更詳細地報告行銷投資。 費用類別在預算建立期間通過樹的&#x200B;**[!UICONTROL Budgets]**&#x200B;節點定義。

若要新增類別，請按一下視窗下方區段的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕。

![](assets/s_user_budget_category.png)

您可以從現有類別中選取類別，或直接在欄位中輸入新類別以定義新類別。 確認輸入時，確認訊息可讓您將此類別新增至現有類別清單，並視需要將其與「自然」建立關聯。 這些資訊將用於預算報告。

### 將預算連結到另一個預算 {#linking-a-budget-to-another}

您可以將預算連結到主預算。 要執行此操作，請在輔助預算的&#x200B;**[!UICONTROL related budget]**&#x200B;欄位中選擇主預算。

![](assets/budget_link.png)

主預算中將添加一個附加標籤，以顯示相關預算的清單。

![](assets/budget_link_new_tab.png)

這些資訊將轉存到預算報告中。

## 添加費用行 {#adding-expense-lines}

費用行會自動添加到預算中。 這些變數會在傳遞分析期間和任務完成時建立。

![](assets/s_ncs_user_budget_line_edit.png)

對於每個促銷活動、交付或任務，生成的成本將按預算的支出行分組，這些支出行將被計入。 這些費用行根據相關服務提供商的成本行建立，並通過相關的成本結構計算。

因此，每個支出行包含以下資訊：

* 促銷活動及其相關的傳遞或任務
* 根據成本結構或估計臨時成本計算的金額
* 交付或相關任務的實際成本
* 對應的發票行（僅MRM）
* 按成本類別計算的成本清單（如果存在成本結構）

在上述範例中，編輯的費用行包含為&#x200B;**忠誠度彈簧包**&#x200B;促銷活動的&#x200B;**新卡**&#x200B;傳送計算的成本。 編輯傳送時， **[!UICONTROL Direct Mail]**&#x200B;標籤可讓您查看費用行的計算方式。

此交付的成本計算基於為有關服務提供商選擇的成本類別：

![](assets/s_user_edit_del_supplier_costs.png)

根據所選成本類別，應用相應的成本結構以計算成本行。 在本例中，對於相關服務提供商，成本結構如下：

![](assets/s_user_edit_node_supplier_costs.png)

>[!NOTE]
>
>成本類別和結構在[建立服務提供商及其成本類別](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)中顯示。

## 成本承諾、計算及收費 {#cost-commitment--calculation-and-charging}

可承諾交付和任務的成本。 根據與其相關的過程的進度，更新成本的狀態。

### 成本計算過程 {#cost-calculation-process}

成本分為三類：

1. 估計臨時費用

   估計的臨時費用是宣傳過程費用的估計。 只要正在編輯，輸入的金額就不會合併。 它必須具有&#x200B;**[!UICONTROL Specified]**&#x200B;狀態，才會在計算中考慮輸入的金額。

   此金額是手動輸入，可細分為數個費用類別。 若要降低成本，請按一下&#x200B;**[!UICONTROL Breakdown...]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以定義新金額。

   ![](assets/s_user_edit_budget_tab_ventil.png)

   您可以將每個成本與某個類別關聯，以便以後可以在相關預算和預算報表中查看按費用類別列出的成本細分。

1. 計算成本

   計算的成本取決於相關元素（促銷活動、傳送、任務等） 及其狀態（正在編輯、進行中、已完成）。 在任何情況下，如果指定了實際成本，則計算成本將使用此金額。

   如果未提供實際成本，則適用下列規則：

   * 對於正在編輯的促銷活動，計算成本是促銷活動的估計臨時成本，如果未定義此成本，則計算成本將是傳送和促銷活動任務的所有臨時成本的總和。 如果促銷活動完成，則促銷活動的計算成本將是所有計算成本的總和。
   * 對於尚未分析的交付，計算成本為估計臨時成本。 如果已執行分析，則計算成本將是從服務提供成本結構計算的所有成本和目標接收者數量的總和。
   * 對於正在進行的任務，計算成本使用估計的臨時成本。 如果任務完成，則計算成本將是從服務提供商成本結構計算的所有成本和完成天數的總和。
   * 對於行銷計畫，至於方案，計算成本是為行銷活動計算的成本總和。 如果沒有指定這些費用，計算的費用將使用估計的臨時費用。

   >[!NOTE]
   >
   >**[!UICONTROL Breakdown]**&#x200B;連結可讓您檢視計算的詳細資訊以及最後的成本計算日期。

1. 實際成本

   實際成本是手動輸入的，如果需要，則會細分為不同的費用類別。

### 計算和計費 {#calculation-and-charging}

成本通過成本結構計算，並計入在相關促銷活動、交付或任務中選擇的預算。

您可以透過預算核准，對提交至促銷活動的金額執行檢查。 可以在促銷活動中建立其他查核點樣式的工作，以設定其他核准。 請參閱[任務類型](../../mrm/using/creating-and-managing-tasks.md#types-of-task)。

### 範例 {#example}

我們將使用：

* 使用服務提供商的成本結構的直接郵件傳送
* 具有固定成本的任務
* 每日成本的任務

#### 步驟1 — 建立預算 {#step-1---creating-the-budget}

1. 透過&#x200B;**[!UICONTROL Campaign management > Budgets]**&#x200B;節點建立新預算。

1. 在&#x200B;**[!UICONTROL Amounts]**&#x200B;節的&#x200B;**[!UICONTROL Allocated]**&#x200B;欄位中定義10,000歐元的預算。 在窗口的下部添加兩個支出類別：

![](assets/s_user_cost_mgmt_sample_1.png)

#### 步驟2 — 配置服務提供商並定義成本結構 {#step-2---configuring-the-service-provider-and-defining-the-cost-structures}

1. 從&#x200B;**[!UICONTROL Administration > Campaigns]**&#x200B;節點建立服務提供商和服務模板及其成本結構。 有關詳細資訊，請參閱[建立服務提供商及其成本類別](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

   對於直接郵件傳遞，建立成本類別&#x200B;**[!UICONTROL Envelopes]**（類型114x229和162x229）、**[!UICONTROL Postage]**&#x200B;和&#x200B;**[!UICONTROL Print]**（類型A3和A4）。 然後建立以下成本結構：

   ![](assets/s_user_cost_mgmt_sample_2.png)

1. 添加固定成本（在成本類別中），其計算是固定的，其金額為空（在相應的成本結構中），並且將為每個交貨單獨指定。

   ![](assets/s_user_cost_mgmt_sample_5.png)

   對於任務，請建立以下兩個成本類別：

   * **[!UICONTROL Room reservation]** （小房間和大房間）, **** 固定費用結構為300和500歐元：

   ![](assets/s_user_cost_mgmt_sample_6.png)

   * **[!UICONTROL Creation]** (**內容** 範本類型)，每日 **** 成本結構為300歐元：

   ![](assets/s_user_cost_mgmt_sample_7.png)

#### 步驟3 — 在促銷活動中扣除預算 {#step-3---charging-the-budget-in-the-campaign}

1. 建立促銷活動並選取步驟1中建立的預算。

   >[!NOTE]
   >
   >依預設，為方案選取的預算會套用至方案中的所有促銷活動。

   ![](assets/s_user_cost_mgmt_sample_4.png)

1. 指定預計的臨時成本，並加以劃分：

   ![](assets/s_user_cost_mgmt_sample_9.png)

1. 按一下&#x200B;**[!UICONTROL Ok]**，然後按一下&#x200B;**[!UICONTROL Save]**&#x200B;以確認此資訊。 然後，將使用估計臨時成本更新該促銷活動的計算成本。

#### 步驟4 — 建立直接郵件傳送 {#step-4---creating-the-direct-mail-delivery}

1. 為促銷活動建立工作流程並定位查詢活動以選取目標（警告，必須指定收件者郵遞區號）。

1. 建立直接郵件傳送，並選取在步驟2中建立的服務提供者：系統會自動顯示成本類別。

1. 覆蓋信封的成本並添加固定成本。 也選擇與這些成本有關的類別。

   ![](assets/s_user_cost_mgmt_sample_3.png)

   >[!NOTE]
   >
   >如果未使用其中一個成本類別，則不會產生任何費用。

1. 啟動您剛建立的工作流程以啟動分析並計算成本。

   ![](assets/s_user_cost_mgmt_sample_10.png)

1. 如果已為此促銷活動啟用預算核准，請從控制面板核准預算。 您可以檢查成本類別的審批。

   ![](assets/s_user_cost_mgmt_sample_10b.png)

有關傳送的費用行會新增至促銷活動的&#x200B;**[!UICONTROL Edit > Budget]**&#x200B;標籤中。 編輯它以查看計算的詳細資訊。

![](assets/s_user_cost_mgmt_sample_11.png)

傳送的計算成本會更新為下列資訊：

![](assets/s_user_cost_mgmt_sample_12.png)

在編輯計算成本時，您可以檢查成本細分以及成本計算的狀態和日期。

#### 步驟5 — 建立任務 {#step-5---creating-tasks}

為此促銷活動，我們將添加以前建立成本結構的兩個任務（請參閱[步驟2 — 配置服務提供程式並定義成本結構](#step-2---configuring-the-service-provider-and-defining-the-cost-structures)）。 若要這麼做，請在促銷活動控制面板中按一下&#x200B;**[!UICONTROL Add a task]**&#x200B;按鈕。 為任務命名，然後按一下&#x200B;**[!UICONTROL Save]**。

1. 然後，任務將添加到任務清單中。 您必須編輯它才能進行設定。

1. 在&#x200B;**[!UICONTROL Properties]**&#x200B;標籤中，選擇服務和相應的成本類別：

   ![](assets/s_user_cost_mgmt_sample_14.png)

1. 接下來，按一下任務的&#x200B;**[!UICONTROL Expenses and revenue]**&#x200B;表徵圖並指定估計臨時成本。

   ![](assets/s_user_cost_mgmt_sample_15.png)

   在保存任務後，將指定計算成本，並輸入估計臨時成本的值。

   完成任務（狀態&#x200B;**[!UICONTROL Finished]**）後，計算成本將自動更新為在其成本結構中輸入的大房間成本。 此成本也會顯示在劃分的此類別中。

1. 接下來，根據同一過程建立第二個任務；排程超過五天，且與先前建立的成本結構相關。

   ![](assets/s_user_cost_mgmt_sample_16.png)

   完成任務後，計算成本將以相關成本結構中的值指定，例如，在本例中為1500歐元（5天x 300歐元）:

   ![](assets/s_user_cost_mgmt_sample_17.png)

#### 步驟6 — 更新促銷活動預算狀態 {#step-6---update-the-campaign-budget-status}

設定促銷活動時，可將其設為&#x200B;**[!UICONTROL Specified]**&#x200B;以更新其狀態。 然後，促銷活動的計算成本會指出傳送的計算成本與促銷活動任務的總和：

![](assets/s_user_cost_mgmt_sample_18.png)

#### 預算核准 {#budget-approval}

啟用核准後，特殊連結可讓您從促銷活動控制面板核准預算。 當目標工作流程啟動且需要核准直接郵件傳送時，就會顯示此連結。

![](assets/s_user_cost_mgmt_sample_19.png)

然後，您可以按一下連結來授予或拒絕核准，或者如果已針對此促銷活動啟動通知，則使用通知電子郵件中的連結。

當預算獲得核准且傳送完成時，成本會透過特殊的技術工作流程自動上傳。

## 訂單和發票 {#orders-and-invoices}

在MRM的上下文中，您可以向服務提供商保存訂單並開具發票。 這些訂單和發票的整個生命週期均可透過Adobe Campaign介面管理。

### 訂單建立 {#order-creation}

要與服務提供商保存新訂單，請按一下樹的&#x200B;**[!UICONTROL MRM > Orders]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

指定訂單編號、相關服務提供商和訂單的總金額。

![](assets/s_user_cost_create_order.png)

### 開具和跟蹤發票 {#issuing-and-tracking-invoices}

對於每個服務提供商，您可以保存發票並定義其狀態和費用預算。

發票將建立並儲存在Adobe Campaign樹的&#x200B;**[!UICONTROL MRM > Invoices]**&#x200B;節點中。

![](assets/s_user_cost_create_invoice.png)

發票由發票行組成，發票行的合計允許自動計算金額。 這些行是從&#x200B;**[!UICONTROL Invoice lines]**&#x200B;頁簽手動建立的。 它們可與訂單關聯，以便將資訊上傳至訂單。

![](assets/s_user_cost_invoice_add_line.png)

每個服務提供商的發票顯示在配置檔案的&#x200B;**[!UICONTROL Invoices]**&#x200B;頁簽中：

![](assets/s_ncs_user_invoice_from_supplier.png)

**[!UICONTROL Details]**&#x200B;標籤可讓您顯示發票的內容。

按一下&#x200B;**[!UICONTROL Add]**&#x200B;以建立新發票。
