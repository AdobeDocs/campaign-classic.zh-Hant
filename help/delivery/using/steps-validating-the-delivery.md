---
product: campaign
title: 驗證傳遞
description: 瞭解如何驗證交付
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 5%

---

# 驗證傳遞 {#validating-the-delivery}

![](../../assets/common.svg)

在建立和配置了傳遞後，必須先驗證它，然後才能將它發送到主目標。

操作步驟：

1. **分析交貨**:此步驟允許您準備要傳遞的消息。 [了解更多](#analyzing-the-delivery)。

   分析過程中所應用的規則於 [此部分](#validation-process-with-typologies)。 有關可用驗證模式的詳細資訊，請參閱 [更改審批模式](#changing-the-approval-mode) 的子菜單。

1. **發送校樣**:此步驟允許您控制內容、URL、個性化等。 瞭解詳情 [發送證據](steps-validating-the-delivery.md#sending-a-proof) 和 [定義特定證明目標](steps-defining-the-target-population.md#defining-a-specific-proof-target)。

>[!IMPORTANT]
>
>上述兩個步驟必須在對消息內容進行每次修改後執行。

## 分析交貨 {#analyzing-the-delivery}

分析是計算目標群體並準備交付內容的階段。 完成後，即可發送。

### 啟動分析 {#launching-the-analysis}

1. 要啟動交付分析，請按一下 **[!UICONTROL Send]**。
1. 選取 **[!UICONTROL Deliver as soon as possible]**。

   ![](assets/s_ncs_user_email_del_send.png)

1. 按一下 **[!UICONTROL Analyze]** 手動啟動分析。

   進度欄顯示分析的進度。

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >分析期間使用的驗證規則在 [具有類型的驗證過程](steps-validating-the-delivery.md#validation-process-with-typologies) 的子菜單。

1. 可通過按一下 **[!UICONTROL Stop]**。

   ![](assets/s_ncs_user_wizard_email01_16.png)

   在準備階段不發送任何消息。 因此，您可以啟動或取消分析，而無風險。

   >[!IMPORTANT]
   >
   >運行時，分析將凍結交貨（或證明）。 對交貨（或證據）的任何更改，必須先進行另一分析，然後才能生效。

1. 等待分析完成。

   分析完成後，窗口的上半部分將指示交貨準備是否完成或是否出現錯誤。 列出所有驗證步驟、警告和錯誤。 彩色表徵圖顯示消息類型：
   * 藍色表徵圖表示資訊性消息。
   * 黃色表徵圖表示非臨界處理錯誤。
   * 紅色表徵圖表示嚴重錯誤，導致無法發送傳遞。

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 按一下 **[!UICONTROL Close]** 更正錯誤（如果有）。

1. 進行更改後，重新啟動分析，按一下 **[!UICONTROL Analyze]**。

檢查分析結果後，可按一下 **[!UICONTROL Confirm delivery]** 將消息發送到指定的目標。 通過確認消息，您可以啟動傳遞。

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>按一下 **[!UICONTROL Change the main delivery target]** 連結。 這允許您更改目標總體的定義並重新啟動分析。

### 分析設定 {#analysis-parameters}

的 **[!UICONTROL Analysis]** 頁籤中，您可以定義一組有關在分析階段準備消息的資訊。

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

此頁籤允許訪問以下選項：

* **[!UICONTROL Label and code of the delivery]** :此部分中的選項用於在交貨分析階段計算這些欄位的值。 的 **[!UICONTROL Compute the execution folder during the delivery analysis]** 欄位將計算在分析階段包含此傳遞操作的資料夾的名稱。
* **[!UICONTROL Approval mode]** :此欄位允許您在分析完成後定義人工或自動交付。 驗證模式在 [更改審批模式](#changing-the-approval-mode) 的子菜單。
* **[!UICONTROL Prepare the delivery parts in the database]** :此選項使您能夠提高交付分析效能。 如需詳細資訊，請參閱[本節](#improving-delivery-analysis)。
* **[!UICONTROL Prepare the personalization data with a workflow]** :此選項允許在自動工作流中準備交付中包含的個性化資料，這可使您在執行個性化設定時的效能顯著提高。 有關此的詳細資訊，請參閱 [優化個性化](personalization-fields.md#optimizing-personalization)。
* **[!UICONTROL Start job in a detached process]** :此選項允許您在單獨的進程中啟動交貨分析。 預設情況下，分析函式使用Adobe Campaign應用程式伺服器進程(web nlserver)。 通過選擇此選項，可確保即使在應用程式伺服器出現故障時也能完成分析。
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** :此選項在分析階段將SQL查詢日誌添加到傳遞日誌。
* **[!UICONTROL Ignore personalization scripts during sending]** :此選項允許您繞過在HTML內容中找到的JavaScript指令的解釋。 它們將像在已傳送內容中一樣顯示。 這些指令與 **&lt;%=** 標籤)。

### 提高交付分析效能 {#improving-delivery-analysis}

為加快交貨準備，您可以檢查 **[!UICONTROL Prepare the delivery parts in the database]** 選項。

啟用此選項後，將直接在資料庫內執行交付準備，這會顯著加快分析。

當前，此選項僅在滿足以下條件時才可用：
* 傳遞必須是電子郵件。 目前不支援其他通道。
* 您不得使用中間來源補充或外部工藝路線，只能使用批量交貨工藝路線類型。 您可以檢查 **[!UICONTROL General]** 頁籤 **[!UICONTROL Delivery properties]**。
* 您不能針對來自外部檔案的人口。 對於單個交貨，按一下 **[!UICONTROL To]** 連結 **[!UICONTROL Email parameters]** 檢查一下 **[!UICONTROL Defined in the database]** 的雙曲餘切值。 對於工作流中使用的交貨，請檢查收件人是否 **[!UICONTROL Specified by the inbound event(s)]** 的 **[!UICONTROL Delivery]** 頁籤。
* 您必須使用PostgreSQL資料庫。

### 配置分析優先順序 {#analysis-priority-}

當交貨是市場活動的一部分時， **[!UICONTROL Advanced]** 頁籤 這樣，您就可以組織同一市場活動中交貨的處理訂單。

在發送之前，將分析每個傳送。 分析持續時間取決於傳遞提取檔案。 檔案的大小越重要，分析所花的時間越長，導致以下交貨等待。

的選項 **[!UICONTROL Message preparation by the scheduler]** 讓您在市場活動工作流中排定交貨分析的優先順序。

![](assets/delivery_analysis_priority.png)

如果交付過大，最好為其分配低優先順序，以避免減慢對其他工作流交付的分析。

>[!NOTE]
>
>為確保較大的交付分析不會減慢工作流的進度，您可以通過在 **[!UICONTROL Schedule execution for a time of low activity]**。

## 傳送證明 {#sending-a-proof}

若要檢測訊息設定中可能出現的錯誤，Adobe 強烈建議您配置傳遞驗證階段。要經常性地透過傳送驗證訊息測試收件者，確保核准內容。每次進行變更時都必須傳送驗證訊息，以核准內容。

>[!NOTE]
>
>* 可用的驗證模式詳見 [更改審批模式](steps-validating-the-delivery.md#changing-the-approval-mode)。
>* 證明目標的配置說明如 [定義特定證明目標](steps-defining-the-target-population.md#defining-a-specific-proof-target)。
>


要發送證明，請執行以下步驟：

1. 確保已按照中所述配置了證明目標 [定義特定證明目標](steps-defining-the-target-population.md#defining-a-specific-proof-target)。
1. 按一下 **[!UICONTROL Send a proof]** 按鈕。

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 啟動消息分析。 請參閱 [分析交貨](steps-validating-the-delivery.md#analyzing-the-delivery)。
1. 您現在可以發送交貨(請參閱 [發送交貨](steps-sending-the-delivery.md))。

   一旦發送，證明將顯示在交貨清單中，並自動建立和編號。 如果要訪問其內容和屬性，可以編輯它。 如需關於此項目的詳細資訊，請參閱此[頁面](about-delivery-monitoring.md)。

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >如果為傳遞(HTML和文本)建立了多種格式，則可以選擇要發送到窗口下部證明收件人的郵件格式。

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

您可能希望修改傳遞的內容，因為驗證組在接收證明時發表了任何評論。 進行更改後，必須重新啟動分析，然後再發送另一個證據。 每個新證明都編號並記錄在交貨日誌中。

分析完交貨後，您可以查看通過 **[!UICONTROL Proofs]** 日誌的子頁籤(**[!UICONTROL Audit]** )的正平方根。

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

在最終確定交付內容之前，必須發送盡可能多的證明。 之後，您可以將交貨發送到主目標並關閉驗證週期。

的 **[!UICONTROL Advanced]** 頁籤中，您可以定義證明的屬性。 如果需要，可以覆蓋收件人排除規則。

![](assets/s_ncs_user_wizard_email01_145.png)

可以使用以下選項：

* 第一個選項讓校樣翻倍。
* 以下兩個選項都允許您將位於denylist上的收件人和隔離地址保留在隔離中。 請參閱中主目標的這些選項的說明 [自定義排除設定](steps-defining-the-target-population.md#customizing-exclusion-settings)。 與交貨的目標不同，預設情況下，這些地址被排除，但預設情況下，這些地址會保留為證明的目標。
* 的 **[!UICONTROL Keep the delivery code for the proof]** 選項，您可以為證明提供與其相關的交貨定義的交貨代碼相同的交貨代碼。 此代碼在傳遞嚮導的第一步中指定。
* 預設情況下，證明的主題以「證明號」為前置詞，其中#是證明號。 您可以在 **[!UICONTROL Label prefix]** 的子菜單。

## 具有類型的驗證過程 {#validation-process-with-typologies}

在發送任何消息之前，您應分析市場活動以批准其內容和配置。 在分析階段應用的檢查規則在 **類型學**。 預設情況下，對於電子郵件，分析涵蓋以下幾點：

* 批准對象
* 批准URL和影像
* 批准URL標籤
* 正在批准取消訂閱連結
* 檢查校樣的大小
* 檢查有效期
* 檢查波次的調度

在中選擇要應用於每個交貨的類型 **[!UICONTROL Typologies]** 的子菜單。

您可以通過以下方式查看和編輯批准規則、其內容、其執行順序以及其完整說明 **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** 的下界。

您可以從此節點建立新規則並定義新類型。 但是，這些任務是為瞭解JavaScript的專家用戶保留的。

有關類型規則的詳細資訊，請參閱 [此頁](../../campaign-opt/using/about-campaign-typologies.md)。

要編輯當前類型，請按一下 **[!UICONTROL Edit link]** 表徵圖 **[!UICONTROL Typology]** 的子菜單。

![](assets/s_ncs_user_email_del_typo_tab.png)

的 **[!UICONTROL Rule]** 頁籤提供要應用的類型規則的清單。 選擇規則，然後按一下 **[!UICONTROL Detail...]** 表徵圖，查看其配置：

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 類型在銷售壓力管理框架內使用。 如需詳細資訊，請參閱[本章節](../../mrm/using/about-marketing-resource-management.md)。

## 更改審批模式 {#changing-the-approval-mode}

的 **[!UICONTROL Analysis]** 的子菜單。 如果在分析期間生成警告（例如，如果某些字元在傳遞的主題中突出等），則可以配置傳遞以定義是否仍應執行它。 預設情況下，用戶必須確認在分析階段結束時發送消息：這是 **手** 驗證。

從相應欄位的下拉清單中選擇另一個批准模式。

![](assets/s_ncs_user_email_del_validation_mode.png)

可使用以下審批模式：

* **[!UICONTROL Manual]**:在分析階段結束時，用戶必須確認發送開始。 要執行此操作，請按一下 **[!UICONTROL Start]** 按鈕啟動交貨。
* **[!UICONTROL Semi-automatic]**:如果分析階段未生成警告消息，則自動開始發送。
* **[!UICONTROL Automatic]**:發送在分析階段結束時自動開始，而與其結果無關。
