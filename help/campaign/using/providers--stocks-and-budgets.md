---
title: 供應商、庫存和預算
seo-title: 供應商、庫存和預算
description: 供應商、庫存和預算
seo-description: null
page-status-flag: never-activated
uuid: 6caffaaf-a6a6-40e1-8b17-07c81748382c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: d4627141-cef1-4ddb-ad6a-5dc217b9fa96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 供應商、庫存和預算{#providers-stocks-and-budgets}

Adobe Campaign可讓您定義將參與促銷活動中所執行工作的服務供應商。 有關服務供應商和相關成本結構的資訊，由Adobe Campaign管理員從主檢視中定義。 服務提供商從交付中引用，其成本結構允許計算與此交付相關的成本以及管理相關庫存。

## 建立服務提供商及其成本結構 {#creating-service-providers-and-their-cost-structures}

每個服務提供商都保存在包含聯繫詳細資訊、服務模板和相關作業的檔案中。

在樹的節點中配置 **[!UICONTROL Administration > Campaign management]** 了服務提供器。

在交付期間執行的任務由服務提供商執行，特別是直接郵件和移動通道。 例如，這些服務提供商可以參與打印或分發消息。 這些作業涉及每個服務提供商專屬的配置和成本。 服務提供商的配置包括四個階段：

1. 在Adobe Campaign中建立服務供應商

   請參 [閱添加服務提供商](#adding-a-service-provider)。

1. 定義相關服務模板的成本類別和結構

   請參 [閱定義成本類別](#defining-cost-categories)[和定義成本結構](#defining-the-cost-structure)。

1. 流程配置

   請參 [閱配置與服務關聯的進程](#configuring-processes-associated-with-a-service)。

1. 在促銷活動層級參考服務提供者

   請參 [閱將服務與促銷活動關聯](#associating-a-service-with-a-campaign)。

### 建立服務提供商及其成本類別 {#creating-a-service-provider-and-its-cost-categories}

#### 添加服務提供商 {#adding-a-service-provider}

您可以視需要為傳送建立任意數量的服務供應商。 添加服務提供方的過程如下：

1. 按一下右鍵服務提供商清單並選擇 **[!UICONTROL New]**，或按一下服務 **[!UICONTROL New]** 提供商清單上方的按鈕。
1. 在窗口的下半部分，指定服務提供商的名稱和聯繫詳細資訊。

   ![](assets/s_ncs_user_supplier_node_01.png)

1. 按一下該 **[!UICONTROL Save]** 按鈕可將服務提供商添加到清單中。

#### 定義成本類別 {#defining-cost-categories}

您必須將服務模板與每個服務提供商關聯。 在這些模板中，您必須首先確定成本類別和相關庫存（如果需要）。 然後，您必須通過成本結構為每個類別建立成本計算規則。

>[!NOTE]
>
>有關詳情，請參閱：定 [義成本結構](#defining-the-cost-structure)。

成本類別是指包含一組符合遞送類型（電子郵件、直效郵件等）資格的成本的實體。或是任務。 成本類別被分組到與服務提供商相關的服務模板中。 每個服務提供商都可以參考一個或多個服務模板。

要建立服務模板並定義其內容，請應用以下步驟：

1. 在服務提 **[!UICONTROL Services]** 供方的頁籤中，按一下該按 **[!UICONTROL Add]** 鈕並命名服務模板。

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. 為每種流程類型（通過直接郵件／電子郵件等發送）建立成本類別。 或工作)。 要執行此操作，請按一下標 **[!UICONTROL Cost categories]** 簽，然後單 **[!UICONTROL Add]** 擊按鈕，然後輸入每個成本類別的參數。

   ![](assets/s_ncs_user_supplier_node_03.png)

   * 輸入此成本類別的標籤，然後選擇相關的流程類型：透過、 **[!UICONTROL Direct mail]**、 **[!UICONTROL E-mail]**、、 **[!UICONTROL Mobile]****[!UICONTROL Telephone]**&#x200B;或傳送 **[!UICONTROL Fax]****[!UICONTROL Task]**。
   * 按一下按 **[!UICONTROL Add]** 鈕可定義與此類別關聯的成本類型。
   * 如有必要，請將庫存行與每種成本類型關聯，以便使用的數量將自動與現有庫存關聯。

      >[!NOTE]
      >
      >庫存行在節點中定 **[!UICONTROL Stock management]** 義。\
      >有關詳情，請參閱「 [Stock and order management」](#stock-and-order-management)。

1. 您可以預先為此成本類別選擇一個值，該值將預設在服務提供商成本類別中提供（而不是空白）。 要執行此操作，請在列中為相關類 **[!UICONTROL Selected]** 別類型選擇選項：

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   在傳送層級，預設會選取值：

   ![](assets/s_ncs_user_supplier_default_cost.png)

### 定義成本結構 {#defining-the-cost-structure}

對於每種成本類型，成本結構指定要應用的計算規則。

按一下標 **[!UICONTROL Cost structure]** 簽可配置每個成本類別和類型的成本計算。 按一下 **[!UICONTROL Add]** 並輸入成本結構。

![](assets/s_ncs_user_supplier_node_04.png)

* 要建立成本結構，請從下拉清單中選擇消息類型和相關的成本類別，以及將應用計算規則的成本類型。 這些下拉式清單的內容來自透過標籤輸入的 **[!UICONTROL Cost categories]** 資訊。

   您必須為成本結構指定標籤。 依預設，它具有下列傳送大綱：成 **本類別——成本類型**。

   不過，您可以重新命名它：直接在欄位中輸入所需 **[!UICONTROL Label]** 值。

* 成本計算公式定義在窗口的下部。

   此公式可以是固定的（對於任意數目的消息）或根據消息數計算。

   當它取決於消息數時，成本計算結構可以是 **[!UICONTROL Linear]**、 **[!UICONTROL Linear by threshold]**&#x200B;或 **[!UICONTROL Constant by threshold]**。

#### 線性結構 {#linear-structure}

如果消息（或消息批）的金額始終相同，而與消息總數無關，請選擇並輸 **[!UICONTROL Linear]** 入每條消息的成本。

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

如果此金額適用於一批消息，請指定欄位中涉及的消息 **[!UICONTROL for]** 數。

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### 基於閾值的線性結構 {#linear-structure-by-threshold}

如果金額按每條消息的閾值應用，則必須定義計算 **[!UICONTROL Linear by threshold]** 結構。 在這種成本結構中，每條消息的成本為0.13，例如，如果消息總數介於1到100之間，則成本為0.12，從100到1000條消息，或從1000條消息到1000條消息，成本為0.11。

配置如下：

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

若要新增臨界值，請按一 **[!UICONTROL Add]** 下清單右側的按鈕。

#### 按閾值的恆定結構 {#constant-structure-by-threshold}

最後，您可以根據消息總數配置成本計算。 要執行此操作，請選擇一個計 **[!UICONTROL Constant by threshold]** 算結構。 例如，將1到100條訊息的成本設為固定金額12.00，傳送101到1000條訊息的成本設為100.00，傳送1000條以上訊息的成本設為500.00，不論傳送總數為何。

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### 配置與服務相關的進程 {#configuring-processes-associated-with-a-service}

您可以通過頁籤關聯與服務相關的進程的 **[!UICONTROL Processes]** 資訊。

要執行此操作，請單 **[!UICONTROL Processes]** 擊頁籤配置向路由器發送資訊。

![](assets/s_ncs_user_supplier_node_02.png)

* 該部 **[!UICONTROL File extraction]** 分指明在選擇此服務時用於交付的導出模板。 您可以在欄位中指定輸出檔案的名 **[!UICONTROL Extraction file]** 稱。 欄位右側的按鈕可讓您插入變數。

   ![](assets/s_ncs_user_supplier_node_02a.png)

* 該 **[!UICONTROL Notification e-mail]** 部分可讓您指定範本，以在傳送檔案後通知服務供應商。 選擇用於建立警報消息的模板和接收者組。

   預設情況下，通知消息的傳送模板將保存在節點中， **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 該節點可從常規視圖訪問。

* 此 **[!UICONTROL Post-processing]** 區段可讓您選取傳送核准後要啟動的工作流程。 如果輸入了工作流模板，工作流實例將自動建立，然後在批准生效後立即啟動。 例如，此工作流程可將擷取檔案傳送至外部服務提供者以進行處理。

### 將服務與促銷活動關聯 {#associating-a-service-with-a-campaign}

服務會透過傳送或工作與促銷活動關聯。 服務供應商會連結至傳送範本，以在透過此範本建立的傳送中提供其服務。

當選擇服務時，與傳送類型（直接郵件、電子郵件等）對應的成本類別會自動在中央表格中指示，以及已定義的處理選項。

>[!NOTE]
>
>如果在選擇服務時未顯示任何成本類別，則表示未為此類流程定義任何成本類別。 例如，對於電子郵件傳送，如果未定義 **[!UICONTROL E-mail]** 任何類型成本類別，則不會顯示任何類別，而且選擇服務將不會產生任何效果。

* 對於直接郵件發送，您可以從配置窗口中選擇服務。

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* 在行動頻道、傳真或電話上傳送時，會套用相同的選擇模式。
* 對於電子郵件傳送，會從傳送屬性的標 **[!UICONTROL Advanced]** 簽中選取服務，如下列範例所示：

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

此 **[!UICONTROL Amount to surcharge]** 欄可讓您在相關傳送或任務的上下文中新增此類別的成本。

您可以在定義交貨的成本類別期間強制選擇成本類型。 若要這麼做，請選取 **[!UICONTROL A cost type must be selected]**。

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## 庫存與訂單管理 {#stock-and-order-management}

成本類型可與庫存行關聯，以處理警報、跟蹤供應和啟動訂單。

在Adobe Campaign中設定庫存和訂單管理，並在交貨供應不足時提醒營運商的程式如下：

1. 相關服務提供商的庫存建立和引用

   請參 [閱建立庫存](#creating-a-stock)。

1. 添加庫存行

   請參 [閱添加庫存行](#adding-stock-lines)。

1. 在發生警報時通知營運商

   請參 [閱警報營運商](#alerting-operators)。

1. 訂單和供應。

   請參閱 [訂購](#orders)。

### 股票管理 {#stock-management}

Adobe Campaign可在庫存不足或達到最低臨界值時，提醒營運商群組。 庫存水準可通過導 **[!UICONTROL Stocks]** 航區的鏈 **[!UICONTROL Campaigns]** 路 **[!UICONTROL Other choices]** 訪問宇宙連結。

![](assets/s_ncs_user_stocks_view.png)

#### 建立股票 {#creating-a-stock}

應用以下步驟建立新庫：

1. 按一下 **[!UICONTROL Create]** 股票清單上方的按鈕。
1. 輸入Stock的標籤，然後從下拉清單中選擇與其關聯的服務提供商。

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >有關詳情，請參閱「建立服 [務提供商及其成本結構」](#creating-service-providers-and-their-cost-structures)。

#### 添加庫存行 {#adding-stock-lines}

一種坯料包括各種坯料線。 庫存行包含交貨將消耗的初始資源數量。 每個庫存行都指明衝減的數量、庫存數量和訂購數量。

建立庫存時，按一下標 **[!UICONTROL Stock lines]** 簽以添加新行。

![](assets/s_ncs_user_stocks_display_line.png)

建立庫存後，按一下它可進行編輯，並使用其儀表板建立和查看庫存行。

按一下按 **[!UICONTROL Create]** 鈕可定義庫存參數。

![](assets/s_ncs_user_stocks_new_line.png)

* 在欄位中指定初始庫存數 **[!UICONTROL Initial stock]** 量。 系統會自 **[!UICONTROL Consumed]** 動計算 **[!UICONTROL In stock]** 和欄位，並隨著促銷活動進度更新欄位。

   ![](assets/s_ncs_user_stocks_create_line.png)

* 在欄位中指定應從哪個臨界值提醒運算子訂購 **[!UICONTROL Alert level]** 庫存。 到達警報級別時，使用此庫存的交貨的審批窗口中將顯示警告消息。

#### 將庫存與成本類別關聯 {#associating-a-stock-with-cost-categories}

對於給定服務提供商，在服務中，庫存行可以由成本類別之一引用，如下所示：

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### 庫存追蹤 {#stock-tracking}

#### 提醒營運商 {#alerting-operators}

當傳送中參考的庫存不足時，會顯示警報。 例如，當抽取檔案獲得核準時，將會顯示下列警報：

![](assets/s_ncs_user_stocks_valid_alert.png)

#### 訂購 {#orders}

子標 **[!UICONTROL Orders]** 簽可讓您檢視目前的訂單並儲存新訂單。

![](assets/s_ncs_user_stocks_edit_from_board.png)

要保存訂單，請編輯目標庫存行，按一下按 **[!UICONTROL Add]** 鈕並指定交貨日期和訂購數量。

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>到達交貨日期後，訂購的庫存行將自動消失，並將在欄位中輸入的數 **[!UICONTROL Volume on order]** 量添加到標籤 **[!UICONTROL Tracking]** 中。 此數量會自動添加到庫存量中。

![](assets/s_ncs_user_stocks_node_08.png)

標籤 **[!UICONTROL Consumptions]** 包含每個促銷活動所耗用的量。 系統將根據執行的交貨自動輸入此標籤中的資訊。 按一下按 **[!UICONTROL Edit]** 鈕以開啟相關的促銷活動。

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## 計算預算 {#calculating-budgets}

### 原則 {#principle}

系統會管理傳送和促銷活動的成本。 根據進度，這些成本會分配至預算。

促銷活動的傳送成本會在促銷活動層級進行整合，而方案的所有促銷活動的成本會傳送至與其關聯的方案。 專屬報表可讓您追蹤整個平台或每個計畫及每個方案的預算。

### 實作 {#implementation}

在促銷活動中，當您選擇預算時，必須輸入初始金額。 計算成本將根據所輸入金額（支出、預計、保留、承諾）的承付水準自動更新。 請參 [閱計算金額](../../campaign/using/controlling-costs.md#calculating-amounts)。

>[!NOTE]
>
>建立預算的過程在建立預 [算中顯示](../../campaign/using/controlling-costs.md#creating-a-budget)。

