---
solution: Campaign Classic
product: campaign
title: 行銷宣傳範本
description: 行銷宣傳範本
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---


# 建立和設定促銷活動範本{#campaign-templates}

所有行銷宣傳都以儲存主要特性與功能的範本為基礎。 促銷活動範本集中在&#x200B;**[!UICONTROL Resources > Templates > Campaign templates]**&#x200B;節點中。 預設範本會以標準形式提供。 它可讓您使用所有可用模組（檔案、工作、種子位址等）建立新促銷活動，但提供的模組取決於您的權限和您的Adobe Campaign平台組態。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>按一下首頁上的&#x200B;**[!UICONTROL Explorer]**&#x200B;表徵圖時將顯示樹。

提供內建範本，以建立尚未定義特定設定的促銷活動。 您可以建立和設定促銷活動範本，然後從這些範本建立促銷活動。

![](assets/do-not-localize/how-to-video.png) 如需建立促銷活動的詳細資訊，請參閱 [此影片](../../campaign/using/marketing-campaign-deliveries.md#create-email-video)。

## 建立促銷活動範本{#creating-or-duplicating-a-campaign-template}

若要建立促銷活動範本，請遵循下列步驟：

1. 開啟促銷活動&#x200B;**瀏覽器**。
1. 在&#x200B;**資源>範本>促銷活動範本**&#x200B;中，按一下範本清單上方的工具列中的&#x200B;**新增**。

   ![](assets/create_campaign_template_1.png)

1. 輸入新促銷活動範本的標籤。
1. 按一下&#x200B;**保存**&#x200B;並重新開啟模板。
1. 在&#x200B;**編輯**&#x200B;標籤中，輸入&#x200B;**內部名稱**&#x200B;和其他值（如果需要）。
1. 選擇「**進階促銷活動設定**」，將工作流程新增至促銷活動範本。

   ![](assets/create_campaign_template_2.png)

1. 將&#x200B;**定位和工作流程**&#x200B;值變更為&#x200B;**是**。

   ![](assets/create_campaign_template_3.png)

1. 在&#x200B;**定位與工作流程**&#x200B;標籤中，按一下&#x200B;**新增工作流程……**。

   ![](assets/create_campaign_template_4.png)

1. 完成&#x200B;**Label**&#x200B;欄位，然後按一下&#x200B;**Ok**。
1. 根據您的需求建立您的工作流程。
1. 按一下&#x200B;**保存**。 您的範本現在已可用於促銷活動。

您也可以&#x200B;**duplicate**&#x200B;預設範本，以重複使用並調整其設定。

促銷活動範本的各種標籤和子標籤可讓您存取其設定，如[一般設定](#general-configuration)中所述。

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 選擇模組{#select-modules}

**[!UICONTROL Advanced campaign settings...]**&#x200B;連結可讓您根據此範本啟用和停用促銷活動的工作。 選取您要在此範本所建立之促銷活動中啟用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未選擇功能，則與流程相關的元素（菜單、表徵圖、選項、頁籤、子頁籤等） 不會顯示在範本的介面中，也不會顯示在以此範本為基礎的促銷活動中。 促銷活動詳細資料左側的標籤通常與範本中選取的程式一致。 例如，如果未選取&#x200B;**費用和目標**，則基於此範本的促銷活動中將不會顯示對應的&#x200B;**[!UICONTROL Budget]**&#x200B;標籤。

此外，設定視窗的捷徑會新增至促銷活動控制面板。 啟用功能時，直接連結會從促銷活動控制面板提供存取權。

例如，使用下列設定：

![](assets/s_ncs_user_op_template_tab1.4.png)

促銷活動控制面板中會顯示下列連結（**[!UICONTROL Add a task]**&#x200B;連結遺失）:

![](assets/s_ncs_user_op_template_tab1.3ex.png)

只會顯示下列標籤：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

但是，使用這種配置：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

將會顯示下列連結和標籤：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 模組類型{#typology-of-enabled-modules}

* **控制組**

   選取此模組時，會在範本的進階設定和基於此範本的促銷活動中新增另一個標籤。 設定可透過範本定義，或個別定義每個促銷活動。 進一步瞭解[本節](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)中的控制群組。

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **種子地址**

   選取此模組時，會在範本的進階設定和基於此範本的促銷活動中新增另一個標籤。 設定可透過範本定義，或個別定義每個促銷活動。 進一步瞭解[本節](../../delivery/using/about-seed-addresses.md)中的種子位址。

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **檔案**

   選取此模組後，會在範本的&#x200B;**[!UICONTROL Edition]**&#x200B;標籤和依據此範本的促銷活動中新增另一個標籤。 附加的檔案可從範本中新增，或針對每個促銷活動個別新增。 進一步瞭解[本節](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)中的檔案。

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **大綱**

   選取此模組時，**[!UICONTROL Delivery outlines]**&#x200B;子標籤會新增至&#x200B;**[!UICONTROL Documents]**&#x200B;標籤，以定義促銷活動的傳送外框。 進一步瞭解[本節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)中的傳送大綱。

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **定位與工作流程**

   當您選取&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;模組時，會新增標籤，讓您根據此範本為促銷活動建立一或多個工作流程。 您也可以根據此範本，針對每個促銷活動個別設定工作流程。進一步瞭解[本節](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)中的促銷活動工作流程。

   ![](assets/s_ncs_user_op_template_activate_5.png)

   啟用此模組後，會在促銷活動的進階設定中新增標籤，以定義流程執行順序。

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **核准**

   如果選擇&#x200B;**[!UICONTROL Approval]**，則可以選擇要審批的流程以及負責審批的運算子。 進一步瞭解[本節](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)中的核准。

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   您可以選擇是否通過模板高級設定部分的&#x200B;**[!UICONTROL Approvals]**&#x200B;頁籤啟用流程批准。 必須批准為其選擇批准的作業，才能獲得消息傳遞的授權。

   必須將審核者運算子或運算子組關聯到每個啟用的批准。

* **費用與目標**

   選取此模組時，會在範本和促銷活動的詳細資料中新增&#x200B;**[!UICONTROL Budget]**&#x200B;標籤，以便選取相關預算。

   ![](assets/s_ncs_user_op_template_activate_7.png)

## 屬性和執行{#general-configuration}

### 範本屬性{#template-properties}

![](assets/s_ncs_user_op_new_template.png)

當您建立促銷活動範本時，需要輸入下列資訊：

* 輸入模板的&#x200B;**label**:此標籤預設會指派給透過此範本建立的所有促銷活動。
* 從下拉式清單中選取促銷活動&#x200B;**nature**。 此清單中可用的值是保存在&#x200B;**[!UICONTROL natureOp]**&#x200B;枚舉中的值。

   >[!NOTE]
   >
   >有關枚舉的詳細資訊，請參閱[Getting Started](../../platform/using/managing-enumerations.md)部分。

* 選擇&#x200B;**促銷活動類型**:唯一、循環或週期。 依預設，促銷活動範本會套用至獨特的促銷活動。 循環和定期促銷活動詳見[本節](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)。
* 指定促銷活動的持續時間，即促銷活動將發生的天數。 根據此範本建立促銷活動時，促銷活動的開始和結束日期會自動填入。

   如果促銷活動是經常性的，您必須直接在範本中指定促銷活動開始和結束日期。

* 指定模板的&#x200B;**相關程式**:基於此範本的促銷活動將連結至選取的方案。

### 模板執行參數{#template-execution-parameters}

**[!UICONTROL Advanced campaign settings...]**&#x200B;連結可讓您設定範本的進階選項，以處理傳送目標（控制群組、種子位址等） 以及促銷活動測量和工作流程執行的設定。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 追蹤促銷活動執行{#campaign-reverse-scheduling}

您可以建立促銷活動的排程並追蹤成績，例如為特定日期準備事件排程。 促銷活動範本現在可讓您根據促銷活動的結束日期，計算任務的開始日期。

在任務配置框中，轉至&#x200B;**[!UICONTROL Implementation schedule]**&#x200B;區域並選中&#x200B;**[!UICONTROL The start date is calculated based on the campaign end date]**&#x200B;框。 （此處，「開始日期」是任務開始日期）。 轉到&#x200B;**[!UICONTROL Start]**&#x200B;欄位並輸入間隔：此任務將在促銷活動結束日期之前很久開始。 如果您輸入的時段比促銷活動設定為最後，則工作會在促銷活動之前開始。

![](assets/mrm_task_in_template_start_date.png)

當您使用此範本建立促銷活動時，系統會自動計算工作開始日期。 不過，您隨時可以稍後變更。
