---
product: campaign
title: 市場營銷活動模板
description: 市場營銷活動模板
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# 建立及設定行銷活動範本 {#campaign-templates}

![](../../assets/v7-only.svg)

所有市場營銷活動都基於一個模板，該模板儲存了主要特徵和功能。 市場活動模板集中在 **[!UICONTROL Resources > Templates > Campaign templates]** 的下界。 預設模板是標準模板。 它允許您使用所有可用模組（文檔、任務、種子地址等）建立新市場活動，但提供的模組取決於您的權限和您的Adobe Campaign平台的配置。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>按一下 **[!UICONTROL Explorer]** 表徵圖

提供內建範本，以建立尚未定義特定設定的行銷活動。 您可以建立和設定行銷活動範本，然後從這些範本建立行銷活動。

![](assets/do-not-localize/how-to-video.png) 有關市場活動建立的詳細資訊，請參閱 [這個視頻](../../campaign/using/marketing-campaign-deliveries.md#create-email-video)。

## 建立市場活動模板 {#creating-or-duplicating-a-campaign-template}

要建立市場活動模板，請執行以下步驟：

1. 開啟市場活動 **瀏覽器**。
1. 在 **資源>模板>市場活動模板**&#x200B;按一下 **新建** 的上界。

   ![](assets/create_campaign_template_1.png)

1. 輸入新市場活動模板的標籤。
1. 按一下 **保存** 重新開啟模板。
1. 在 **編輯** 的 **內部名稱** 和其他價值。
1. 選擇 **高級市場活動設定** 將工作流添加到市場活動模板。

   ![](assets/create_campaign_template_2.png)

1. 更改 **目標和工作流** 值 **是**。

   ![](assets/create_campaign_template_3.png)

1. 在 **目標和工作流** 按鈕 **添加工作流……**。

   ![](assets/create_campaign_template_4.png)

1. 完成 **標籤** 按一下 **確定**。
1. 根據您的要求建立您的工作流。
1. 按一下 **保存**。 您的模板現已準備好用於市場活動。

您也可以 **重複** 要重新使用和調整其配置的預設模板。

市場活動模板的各個標籤和子標籤允許您訪問其設定，如中所述 [常規配置](#general-configuration)。

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 選擇模組 {#select-modules}

的 **[!UICONTROL Advanced campaign settings...]** 連結允許您基於此模板為市場活動啟用和禁用職務。 選擇要在基於此模板建立的市場活動中啟用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未選擇功能，則與流程相關的元素（菜單、表徵圖、選項、制表符、子制表符等） 將不顯示在模板的介面或基於此模板的市場活動中。 市場活動詳細資訊左側的標籤通常與模板中選擇的流程一致。 例如，如果 **費用和目標** 未選擇，對應 **[!UICONTROL Budget]** 頁籤將不顯示在基於此模板的市場活動中。

此外，配置窗口的快捷方式被添加到市場活動儀表板。 啟用功能後，直接連結將允許從市場活動控制面板訪問該功能。

例如，使用以下配置：

![](assets/s_ncs_user_op_template_tab1.4.png)

市場活動控制面板中顯示以下連結( **[!UICONTROL Add a task]** 連結丟失):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

只顯示以下頁籤：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

但是，使用此類配置：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

將顯示以下連結和頁籤：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 模組類型 {#typology-of-enabled-modules}

* **控制組**

   選擇此模組後，將在模板的高級設定和基於此模板的市場活動中添加附加標籤。 可以通過模板定義配置，也可以針對每個市場活動單獨定義配置。 瞭解有關中的控制組的詳細資訊 [此部分](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **種子地址**

   選擇此模組後，將在模板的高級設定和基於此模板的市場活動中添加附加標籤。 可以通過模板定義配置，也可以針對每個市場活動單獨定義配置。 瞭解有關中的種子地址的詳細資訊 [此部分](../../delivery/using/about-seed-addresses.md)。

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **文檔**

   選擇此模組後，將向 **[!UICONTROL Edition]** 的子菜單。 可以從模板中添加附加文檔，也可以為每個市場活動單獨添加附加文檔。 瞭解有關中文檔的詳細資訊 [此部分](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)。

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **大綱**

   選擇此模組時， **[!UICONTROL Delivery outlines]** 頁籤添加到 **[!UICONTROL Documents]** 的子菜單。 瞭解有關中的交付大綱的詳細資訊 [此部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **目標和工作流**

   選擇 **[!UICONTROL Targeting and workflows]** 模組中，將添加一個頁籤，以便您基於此模板為市場活動建立一個或多個工作流。 也可以根據此模板為每個市場活動單獨配置工作流。瞭解有關市場活動工作流的詳細資訊，請參閱 [此部分](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。

   ![](assets/s_ncs_user_op_template_activate_5.png)

   啟用此模組後，會向市場活動的高級設定中添加一個頁籤，以定義流程執行順序。

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **核准**

   如果選擇 **[!UICONTROL Approval]**，您可以選擇要審批的流程以及負責審批的操作員。 瞭解有關批准的詳細資訊 [此部分](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)。

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   您可以選擇是否通過 **[!UICONTROL Approvals]** 頁籤。 要授權郵件傳遞，必須批准選定審批的作業。

   必須將審閱者運算子或運算子組與每個已啟用的審批相關聯。

* **費用和目標**

   選擇此模組時， **[!UICONTROL Budget]** 頁籤將添加到模板和基於此模板的市場活動的詳細資訊中，以便可以選擇關聯的預算。

   ![](assets/s_ncs_user_op_template_activate_7.png)

## 屬性和執行 {#general-configuration}

### 模板屬性 {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

建立市場活動模板時，需要輸入以下資訊：

* 輸入 **標籤** 的下界：預設情況下，此標籤將分配給通過此模板建立的所有市場活動。
* 選擇市場活動 **性** 從下拉清單中。 此清單中可用的值是保存在 **[!UICONTROL natureOp]** 枚舉。

   >[!NOTE]
   >
   >有關枚舉的詳細資訊，請參閱 [入門](../../platform/using/managing-enumerations.md) 的子菜單。

* 選擇 **市場活動類型**:唯一、循環或定期。 預設情況下，市場活動模板適用於唯一的市場活動。 定期市場活動和定期市場活動的詳細資訊請參閱 [此部分](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)。
* 指定市場活動的持續時間，即市場活動將發生的天數。 在基於此模板建立市場活動時，將自動填充市場活動起始日期和終止日期。

   如果市場活動是經常性的，則必須直接在模板中指定市場活動起始日期和終止日期。

* 指定 **相關計畫** 的下界：基於此模板的市場活動將連結到選定的計畫。

### 模板執行參數 {#template-execution-parameters}

的 **[!UICONTROL Advanced campaign settings...]** 連結允許您配置模板的高級選項以處理傳遞目標（控制組、種子地址等） 以及市場活動測量和工作流執行的配置。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 跟蹤市場活動執行{#campaign-reverse-scheduling}

您可以為市場活動建立計畫並跟蹤成績，例如為特定日期準備事件計畫。 市場活動模板現在允許您根據市場活動的結束日期計算任務的起始日期。

在任務配置框中，轉到 **[!UICONTROL Implementation schedule]** 的 **[!UICONTROL The start date is calculated based on the campaign end date]** 框。 （此處，「開始日期」是任務開始日期）。 轉到 **[!UICONTROL Start]** 欄位並輸入間隔：該任務將在市場活動結束日期之前很久開始。 如果輸入的期間長於市場活動設定為最後的期間，則任務將在市場活動之前開始。

![](assets/mrm_task_in_template_start_date.png)

使用此模板建立市場活動時，將自動計算任務起始日期。 但是，您總是可以稍後更改。
