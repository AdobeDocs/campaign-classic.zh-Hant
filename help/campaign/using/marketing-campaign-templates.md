---
product: campaign
title: 行銷活動範本
description: 行銷活動範本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 4%

---

# 建立及設定行銷活動範本 {#campaign-templates}

所有行銷活動都以儲存主要特性和功能的範本為基礎。 行銷活動範本集中於 **[!UICONTROL Resources > Templates > Campaign templates]** 節點。 預設範本以標準形式提供。 它可讓您使用所有可用的模組（檔案、任務、種子地址等）建立新的行銷活動，但提供的模組取決於您的許可權和Adobe Campaign平台的設定。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>當您按一下 **[!UICONTROL Explorer]** 圖示加以檢視。

提供內建範本，以建立尚未定義特定設定的行銷活動。 您可以建立和設定行銷活動範本，然後從這些範本建立行銷活動。

![](assets/do-not-localize/how-to-video.png) 如需建立行銷活動的詳細資訊，請參閱 [此影片](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## 建立行銷活動範本 {#creating-or-duplicating-a-campaign-template}

若要建立行銷活動範本，請遵循下列步驟：

1. 開啟行銷活動 **總管**.
1. 在 **資源>範本>行銷活動範本**，按一下 **新增** 範本清單上方的工具列中。

   ![](assets/create_campaign_template_1.png)

1. 輸入新行銷活動範本的標籤。
1. 按一下 **儲存** 並重新開啟範本。
1. 在 **編輯** 索引標籤中，輸入 **內部名稱** 和其他值（如有需要）。
1. 選取 **進階行銷活動設定** 以將工作流程新增至行銷活動範本。

   ![](assets/create_campaign_template_2.png)

1. 變更 **目標定位和工作流程** 值至 **是**.

   ![](assets/create_campaign_template_3.png)

1. 在 **目標定位和工作流程** 標籤，按一下 **新增工作流程……**.

   ![](assets/create_campaign_template_4.png)

1. 完成 **標籤** 欄位並按一下 **確定**.
1. 根據您的要求建立工作流程。
1. 按一下「**儲存**」。您的範本現在已準備好用於行銷活動。

您也可以 **重複** 預設範本以重複使用並調整其設定。

行銷活動範本的各種標籤和子標籤可讓您存取其設定，如所述 [一般設定](#general-configuration).

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 選取模組 {#select-modules}

此 **[!UICONTROL Advanced campaign settings...]** 連結可讓您根據此範本為行銷活動啟用和停用工作。 選取您要在根據此範本建立的行銷活動中啟用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未選取權能，則與流&#39;b5&#39;7b有關的元素（選單、圖示、選項、標籤、子標籤等） 將不會顯示在範本的介面或根據此範本的行銷活動中。 行銷活動詳細資料左側的標籤通常與範本中選取的程式一致。 例如，如果 **費用與目標** 未選取，則對應至 **[!UICONTROL Budget]** 索引標籤不會顯示在根據此範本的行銷活動中。

此外，設定視窗的捷徑會新增至行銷活動控制面板。 啟用功能時，直接連結可讓您從行銷活動控制面板存取該功能。

例如，使用下列設定：

![](assets/s_ncs_user_op_template_tab1.4.png)

行銷活動控制面板中會顯示下列連結( **[!UICONTROL Add a task]** 連結遺失)：

![](assets/s_ncs_user_op_template_tab1.3ex.png)

而且只會顯示下列標籤：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

不過，若使用這類設定：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

將顯示下列連結和標籤：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 模組型別 {#typology-of-enabled-modules}

* **控制組**

   選取此模組時，範本的進階設定和根據此範本的行銷活動會新增一個標籤。 可透過範本或為每個行銷活動個別定義設定。 進一步瞭解中的控制組 [本節](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **種子地址**

   選取此模組時，範本的進階設定和根據此範本的行銷活動會新增一個標籤。 可透過範本或為每個行銷活動個別定義設定。 進一步瞭解中的種子地址 [本節](../../delivery/using/about-seed-addresses.md).

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **文件**

   選取此模組時，會將其他索引標籤新增至 **[!UICONTROL Edition]** 標籤以及以此範本為依據的行銷活動。 可從範本新增附加檔案，或針對每個行銷活動個別新增。 進一步瞭解中的檔案 [本節](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **大綱**

   選取此模組時， **[!UICONTROL Delivery outlines]** 子標籤會新增至 **[!UICONTROL Documents]** 索引標籤來定義行銷活動的傳遞大綱。 進一步瞭解中的傳遞大綱 [本節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **目標定位和工作流程**

   當您選取 **[!UICONTROL Targeting and workflows]** 模組，新增了標籤，讓您根據此範本建立一或多個行銷活動的工作流程。 您也可以根據此範本個別設定每個行銷活動的工作流程。進一步瞭解 [本節](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

   ![](assets/s_ncs_user_op_template_activate_5.png)

   啟用此模組後，即會在行銷活動的進階設定中新增索引標籤，以定義流程執行順序。

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **核准**

   如果您選取 **[!UICONTROL Approval]**，您可以選取要核准的程式以及負責核准的運運算元。 進一步瞭解中的核准 [本節](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   您可以選擇是否透過 **[!UICONTROL Approvals]** 「範本進階設定」區段的「 」索引標籤。 選取核准的工作必須經過核准，訊息傳遞才會獲得授權。

   您必須將稽核者操作員或操作員群組與每個啟用的核准建立關聯。

* **費用和目標**

   選取此模組時， **[!UICONTROL Budget]** 索引標籤會新增至範本的詳細資訊以及以此範本為依據的行銷活動，以便選取關聯的預算。

   ![](assets/s_ncs_user_op_template_activate_7.png)

## 屬性和執行 {#general-configuration}

### 範本屬性 {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

建立行銷活動範本時，需要輸入下列資訊：

* 輸入 **標籤** 範本的：依預設，此標籤將指派給透過此範本建立的所有行銷活動。
* 選取行銷活動 **性質** 下拉式清單中的。 此清單中可用的值是儲存在 **[!UICONTROL natureOp]** 分項清單。

   >[!NOTE]
   >
   >如需分項清單的詳細資訊，請參閱 [快速入門](../../platform/using/managing-enumerations.md) 區段。

* 選取 **行銷活動型別**：唯一、循環或定期。 依預設，行銷活動範本適用於不重複行銷活動。 循環和定期行銷活動的詳細資訊，請參見 [本節](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* 指定行銷活動的持續時間，即行銷活動將發生的天數。 根據此範本建立行銷活動時，會自動填入行銷活動的開始和結束日期。

   如果行銷活動為週期性，您必須直接在範本中指定行銷活動的開始和結束日期。

* 指定 **相關程式** 範本的：根據此範本的行銷活動將連結至選取的方案。

### 範本執行引數 {#template-execution-parameters}

此 **[!UICONTROL Advanced campaign settings...]** 連結可讓您設定處理傳遞目標（控制組、種子地址等）的範本進階選項 以及行銷活動測量和工作流程執行的設定。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 追蹤行銷活動執行{#campaign-reverse-scheduling}

您可以建立行銷活動的排程並追蹤成績，例如，為特定日期準備事件排程。 行銷活動範本現在可讓您根據行銷活動的結束日期計算任務的開始日期。

在任務設定方塊中，前往 **[!UICONTROL Implementation schedule]** 區域並檢查 **[!UICONTROL The start date is calculated based on the campaign end date]** 方塊。 （在此，「開始日期」是任務開始日期）。 前往 **[!UICONTROL Start]** 欄位並輸入間隔：此任務將在行銷活動結束日期之前很久開始。 如果您輸入的期間長於促銷活動設為最後的時段，則任務會在促銷活動之前開始。

![](assets/mrm_task_in_template_start_date.png)

使用此範本建立行銷活動時，將自動計算任務開始日期。 不過，您稍後一律可以加以變更。
