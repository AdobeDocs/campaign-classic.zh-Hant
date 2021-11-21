---
product: campaign
title: 驗證傳遞
description: 驗證傳遞
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1663'
ht-degree: 5%

---

# 驗證傳遞 {#validating-the-delivery}

![](../../assets/common.svg)

建立並設定傳送後，您必須先驗證傳送，才能將其傳送至主要目標。

操作步驟：

1. **分析傳送**:此步驟可讓您準備要傳送的訊息。 [深入瞭解](#analyzing-the-delivery)。

   分析期間所套用的規則如下： [本節](#validation-process-with-typologies). 在 [變更核准模式](#changing-the-approval-mode) 區段。

1. **傳送校樣**:此步驟可讓您控制內容、URL、個人化等。 深入了解 [傳送校樣](steps-validating-the-delivery.md#sending-a-proof) 和 [定義特定校樣目標](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>上述兩個步驟必須在對訊息內容進行每次修改後執行。

## 分析傳送 {#analyzing-the-delivery}

分析是計算目標母體並準備傳送內容的階段。 完成傳遞後，即可傳送。

### 啟動分析 {#launching-the-analysis}

1. 若要啟動傳送分析，請按一下 **[!UICONTROL Send]**.
1. 選取 **[!UICONTROL Deliver as soon as possible]**。

   ![](assets/s_ncs_user_email_del_send.png)

1. 按一下 **[!UICONTROL Analyze]** 以手動啟動分析。

   進度列會顯示分析的進度。

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >分析期間使用的驗證規則於 [使用類型驗證程式](steps-validating-the-delivery.md#validation-process-with-typologies) 區段。

1. 您可以隨時按一下「 」以停止分析 **[!UICONTROL Stop]**.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   準備階段期間不會傳送任何訊息。 因此，您可以開始或取消分析，而無風險。

   >[!IMPORTANT]
   >
   >執行時，分析會凍結傳送（或校樣）。 傳送的任何變更（或證明）都必須先進行其他分析，才能適用。

1. 等待分析完成。

   分析完成時，視窗的上方區段會指出傳送準備是否完成或是否發生任何錯誤。 列出所有驗證步驟、警告和錯誤。 彩色表徵圖顯示消息類型：
   * 藍色圖示表示資訊性訊息。
   * 黃色表徵圖表示非關鍵處理錯誤。
   * 紅色圖示表示有嚴重錯誤而無法傳送傳遞。

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 按一下 **[!UICONTROL Close]** 以更正錯誤（如果有）。

1. 進行變更後，請按一下「 」以重新啟動分析 **[!UICONTROL Analyze]**.

檢查分析結果後，您可以按一下 **[!UICONTROL Confirm delivery]** 將消息發送到指定目標。 確認訊息可讓您啟動傳送。

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>按一下 **[!UICONTROL Change the main delivery target]** 如果要傳送的訊息數量不符合您的設定，則連結。 這可讓您變更目標母體的定義並重新開始分析。

### 分析設定 {#analysis-parameters}

此 **[!UICONTROL Analysis]** 傳送屬性的索引標籤，可讓您定義分析階段期間準備訊息的一組資訊。

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

此索引標籤可供存取下列選項：

* **[!UICONTROL Label and code of the delivery]** :本區段中的選項可用來計算傳送分析階段期間這些欄位的值。 此 **[!UICONTROL Compute the execution folder during the delivery analysis]** 欄位會計算在分析階段期間包含此傳送動作的資料夾名稱。
* **[!UICONTROL Approval mode]** :分析完成後，此欄位可讓您定義手動或自動傳送。 驗證模式如下： [變更核准模式](#changing-the-approval-mode) 區段。
* **[!UICONTROL Prepare the delivery parts in the database]** :此選項可讓您改善傳遞分析效能。 如需詳細資訊，請參閱[本節](#improving-delivery-analysis)。
* **[!UICONTROL Prepare the personalization data with a workflow]** :此選項可讓您以自動工作流程準備傳送中包含的個人化資料，讓您在執行個人化時大幅提升效能。 有關詳細資訊，請參閱 [最佳化個人化](personalization-fields.md#optimizing-personalization).
* **[!UICONTROL Start job in a detached process]** :此選項可讓您以個別程式開始傳送分析。 依預設，分析函式會使用Adobe Campaign應用程式伺服器程式(web nlserver)。 通過選擇此選項，您確保即使在應用程式伺服器出現故障時也能完成分析。
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** :此選項會在分析階段期間將SQL查詢日誌添加到傳遞日誌。
* **[!UICONTROL Ignore personalization scripts during sending]** :此選項可讓您略過HTML內容中找到的JavaScript指令的解譯。 它們會如傳送內容中所示顯示。 這些指令與 **&lt;%=** 標籤)。

### 改善傳遞分析效能 {#improving-delivery-analysis}

若要加快傳送準備，您可以檢查 **[!UICONTROL Prepare the delivery parts in the database]** 選項。

啟用此選項時，會直接在資料庫中執行傳送準備，大幅加速分析。

目前，只有在符合下列條件時，才可使用此選項：
* 傳送必須是電子郵件。 目前不支援其他管道。
* 您不得使用中間來源或外部路由，只能使用批量傳送路由類型。 您可以檢查 **[!UICONTROL General]** 的 **[!UICONTROL Delivery properties]**.
* 您無法定位來自外部檔案的母體。 若為單一傳送，請按一下 **[!UICONTROL To]** 連結 **[!UICONTROL Email parameters]** 檢查 **[!UICONTROL Defined in the database]** 選項。 對於工作流程中使用的傳送，請檢查收件者是否 **[!UICONTROL Specified by the inbound event(s)]** 在 **[!UICONTROL Delivery]** 標籤。
* 必須使用PostgreSQL資料庫。

### 設定分析優先順序 {#analysis-priority-}

當傳送屬於促銷活動時， **[!UICONTROL Advanced]** 標籤提供其他選項。 這可讓您組織相同促銷活動中傳送的處理順序。

在傳送前，會分析每個傳送。 分析持續時間取決於傳送擷取檔案。 檔案大小越顯著，分析所花的時間就越長，導致下列傳送等待。

適用於 **[!UICONTROL Message preparation by the scheduler]** 可讓您在行銷活動工作流程中排定傳送分析的優先順序。

![](assets/delivery_analysis_priority.png)

如果傳送過大，最好指派低優先順序給它，以避免拖慢其他工作流程傳送的分析。

>[!NOTE]
>
>為確保大型傳送分析不會拖慢工作流程的進度，您可以借由滴答來排程執行 **[!UICONTROL Schedule execution for a time of low activity]**.

## 傳送證明 {#sending-a-proof}

若要檢測訊息設定中可能出現的錯誤，Adobe 強烈建議您配置傳遞驗證階段。要經常性地透過傳送驗證訊息測試收件者，確保核准內容。每次進行變更時都必須傳送驗證訊息，以核准內容。

>[!NOTE]
>
>* 有關可用驗證模式的詳細資訊，請參閱 [變更核准模式](steps-validating-the-delivery.md#changing-the-approval-mode).
>* 校樣目標的設定說明於 [定義特定校樣目標](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>


若要傳送校樣，請遵循下列步驟：

1. 請確定已依照 [定義特定校樣目標](steps-defining-the-target-population.md#defining-a-specific-proof-target).
1. 按一下 **[!UICONTROL Send a proof]** 在傳遞精靈的頂端列。

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 啟動消息分析。 請參閱 [分析傳送](steps-validating-the-delivery.md#analyzing-the-delivery).
1. 您現在可以傳送傳送(請參閱 [傳送傳送](steps-sending-the-delivery.md))。

   傳送傳遞後，校樣會顯示在傳遞清單中，並自動建立及編號。 如果您想要存取其內容和屬性，可以編輯它。 如需關於此項目的詳細資訊，請參閱此[頁面](about-delivery-monitoring.md)。

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >如果已為傳送建立數種格式(HTML和文字)，您可以在視窗的下方區段中選擇要傳送給校樣收件者的訊息格式。

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

您可能會因為驗證群組收到校樣所做的任何註解，而修改傳送的內容。 進行變更後，您必須重新啟動分析，然後傳送其他校樣。 每個新校樣都會編號並記錄在傳送日誌中。

分析傳送後，您可以檢視透過 **[!UICONTROL Proofs]** 日誌的子頁簽(**[!UICONTROL Audit]** 標籤)。

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

您必須視需要傳送多份校樣，直到傳送內容完成為止。 之後，您可以將傳送傳送至主要目標，並關閉驗證週期。

此 **[!UICONTROL Advanced]** 傳遞屬性的索引標籤可讓您定義校樣的屬性。 如有需要，您可以覆寫收件者排除規則。

![](assets/s_ncs_user_wizard_email01_145.png)

可以使用以下選項：

* 第一個選項可讓您保持校樣加倍。
* 下列兩個選項都可讓您將封鎖清單上的收件者和隔離地址保留在隔離區中。 請參閱 [自訂排除設定](steps-defining-the-target-population.md#customizing-exclusion-settings). 與傳送的目標不同，這些位址預設會排除，預設會保留供校樣的目標使用。
* 此 **[!UICONTROL Keep the delivery code for the proof]** 選項可讓您提供與校樣相關的傳送所定義的傳送代碼。 此程式碼會在傳送精靈的第一個步驟中指定。
* 依預設，校樣的主旨會加上前置詞「校樣#」，其中#代表校樣的編號。 您可以在 **[!UICONTROL Label prefix]** 欄位。

## 使用類型驗證程式 {#validation-process-with-typologies}

傳送任何訊息之前，您應分析促銷活動以核准其內容和設定。 分析階段期間套用的檢查規則會定義於 **類型**. 依預設，對於電子郵件，分析涵蓋下列幾點：

* 核准物件
* 核准URL和影像
* 核准URL標籤
* 核准取消訂閱連結
* 檢查校樣的大小
* 檢查有效期
* 檢查波的調度

在 **[!UICONTROL Typologies]** 索引標籤。

您可以透過 **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** 節點。

您可以從此節點建立新規則並定義新類型。 不過，這些工作會保留給熟悉JavaScript的專家使用者。

如需類型規則的詳細資訊，請參閱 [本頁](../../campaign-opt/using/about-campaign-typologies.md).

若要編輯目前的類型，請按一下 **[!UICONTROL Edit link]** 表徵圖 **[!UICONTROL Typology]** 欄位。

![](assets/s_ncs_user_email_del_typo_tab.png)

此 **[!UICONTROL Rule]** 索引標籤會提供要套用的類型規則清單。 選取規則，然後按一下 **[!UICONTROL Detail...]** 圖示以檢視其設定：

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 在銷售壓力管理的框架內使用類型。 如需詳細資訊，請參閱[本章節](../../mrm/using/about-marketing-resource-management.md)。

## 變更核准模式 {#changing-the-approval-mode}

此 **[!UICONTROL Analysis]** 索引標籤，以供您選取驗證模式。 如果分析期間產生警告（例如，如果傳送的主旨中會強調某些字元等），您可以設定傳送以定義是否應仍執行該傳送。 依預設，使用者必須在分析階段結束時確認訊息的傳送：這是 **手動** 驗證。

從適當欄位的下拉式清單中選取其他核准模式。

![](assets/s_ncs_user_email_del_validation_mode.png)

提供下列核准模式：

* **[!UICONTROL Manual]**:在分析階段結束時，使用者必須確認傳送以開始傳送。 若要這麼做，請按一下 **[!UICONTROL Start]** 按鈕以啟動傳送。
* **[!UICONTROL Semi-automatic]**:如果分析階段未產生警告訊息，則會自動開始傳送。
* **[!UICONTROL Automatic]**:無論結果如何，發送都會在分析階段結束時自動開始。
