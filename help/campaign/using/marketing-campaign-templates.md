---
product: campaign
title: 行銷活動範本
description: 行銷活動範本
role: User
feature: Campaigns, Templates
hide: true
hidefromtoc: true
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 3%

---

# 建立及設定行銷活動範本 {#campaign-templates}

所有行銷活動都以儲存主要特性和功能的範本為基礎。 行銷活動範本集中在&#x200B;**[!UICONTROL Resources > Templates > Campaign templates]**&#x200B;節點。 預設範本是以標準形式提供。 它可讓您使用所有可用的模組（檔案、工作、種子地址等）建立新的行銷活動，但提供的模組取決於您的許可權和Adobe Campaign平台的設定。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>當您按一下首頁上的&#x200B;**[!UICONTROL Explorer]**&#x200B;圖示時，會顯示樹狀結構。

提供內建範本，以建立尚未定義特定設定的行銷活動。 您可以建立和設定行銷活動範本，然後從這些範本建立行銷活動。

![](assets/do-not-localize/how-to-video.png)如需建立行銷活動的詳細資訊，請參閱[此影片](../../campaign/using/marketing-campaign-deliveries.md#create-email-video)。

## 建立行銷活動範本 {#creating-or-duplicating-a-campaign-template}

若要建立行銷活動範本，請遵循下列步驟：

1. 開啟Campaign **總管**。
1. 在&#x200B;**資源>範本>行銷活動範本**&#x200B;中，按一下範本清單上方工具列中的&#x200B;**新增**。

   ![](assets/create_campaign_template_1.png)

1. 輸入新行銷活動範本的標籤。
1. 按一下&#x200B;**儲存**&#x200B;並重新開啟您的範本。
1. 在&#x200B;**編輯**&#x200B;索引標籤中，視需要輸入&#x200B;**內部名稱**&#x200B;和其他值。
1. 選取&#x200B;**進階行銷活動設定**&#x200B;以將工作流程新增至行銷活動範本。

   ![](assets/create_campaign_template_2.png)

1. 將&#x200B;**目標定位和工作流程**&#x200B;值變更為&#x200B;**是**。

   ![](assets/create_campaign_template_3.png)

1. 在&#x200B;**目標定位和工作流程**&#x200B;索引標籤中，按一下&#x200B;**新增工作流程……**。

   ![](assets/create_campaign_template_4.png)

1. 完成&#x200B;**標籤**&#x200B;欄位並按一下&#x200B;**確定**。
1. 根據您的要求建立您的工作流程。
1. 按一下&#x200B;**儲存**。 您的範本現在已準備好用於行銷活動。

您也可以&#x200B;**複製**&#x200B;預設範本以重複使用並調整其設定。

行銷活動範本的各種標籤和子標籤可讓您存取其設定，如[一般設定](#general-configuration)中所述。

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 選取模組 {#select-modules}

**[!UICONTROL Advanced campaign settings...]**&#x200B;連結可讓您根據此範本為行銷活動啟用和停用工作。 選取您要在根據此範本建立的行銷活動中啟用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未選取功能，則與流程相關的元素（功能表、圖示、選項、標籤、子標籤等）將不會顯示在範本的介面或根據此範本的行銷活動中。 行銷活動詳細資訊左側的標籤通常與範本中選取的程式一致。 例如，如果未選取&#x200B;**費用和目標**，則根據此範本的行銷活動中將不會顯示對應的&#x200B;**[!UICONTROL Budget]**&#x200B;標籤。

此外，設定視窗的捷徑會新增至行銷活動控制面板。 啟用功能時，直接連結可讓您從Campaign控制面板存取功能。

例如，使用下列設定：

![](assets/s_ncs_user_op_template_tab1.4.png)

行銷活動控制面板中會顯示下列連結（缺少&#x200B;**[!UICONTROL Add a task]**&#x200B;連結）：

![](assets/s_ncs_user_op_template_tab1.3ex.png)

而且只會顯示下列標籤：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

但是，對於此型別的設定：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

將顯示下列連結和標籤：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 模組型別 {#typology-of-enabled-modules}

* **控制組**

  選取此模組時，範本的進階設定及根據此範本的行銷活動會新增一個標籤。 可透過範本或為每個行銷活動個別定義設定。 在[本節](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)中進一步瞭解控制組。

  ![](assets/s_ncs_user_op_template_activate_1.png)

* **種子地址**

  選取此模組時，範本的進階設定及根據此範本的行銷活動會新增一個標籤。 可透過範本或為每個行銷活動個別定義設定。 在[本節](../../delivery/using/about-seed-addresses.md)中進一步瞭解種子地址。

  ![](assets/s_ncs_user_op_template_activate_2.png)

* **檔案**

  選取此模組時，範本的&#x200B;**[!UICONTROL Edition]**&#x200B;索引標籤及根據此範本的行銷活動會新增一個索引標籤。 可從範本新增附加檔案，或針對每個促銷活動個別新增。 在[本節](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)中進一步瞭解檔案。

  ![](assets/s_ncs_user_op_template_activate_3.png)

* **大綱**

  選取此模組時，會將&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子索引標籤新增至&#x200B;**[!UICONTROL Documents]**&#x200B;索引標籤，以定義行銷活動的傳遞大綱。 在[本節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)中進一步瞭解傳遞大綱。

  ![](assets/s_ncs_user_op_template_activate_4.png)

* **目標定位和工作流程**

  選取&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;模組時，會新增索引標籤，讓您根據此範本建立一或多個行銷活動的工作流程。 您也可以根據此範本個別設定每個行銷活動的工作流程。在[本節](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)中進一步瞭解行銷活動工作流程。

  ![](assets/s_ncs_user_op_template_activate_5.png)

  啟用此模組後，即會將索引標籤新增至行銷活動的進階設定，以定義程式執行順序。

  ![](assets/s_ncs_user_op_template_activate_5a.png)

* **核准**

  如果您選取&#x200B;**[!UICONTROL Approval]**，您可以選取要核准的程式以及負責核准的運運算元。 在[本節](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)中進一步瞭解核准。

  ![](assets/s_ncs_user_op_template_activate_5b.png)

  您可以選擇是否透過&#x200B;**[!UICONTROL Approvals]**&#x200B;索引標籤（範本進階設定區段）啟用程式核准。 選取核准的工作必須核准才能授權訊息傳送。

  您必須將稽核者操作員或操作員群組與每個啟用的核准建立關聯。

* **費用和目標**

  選取此模組時，會根據此範本將&#x200B;**[!UICONTROL Budget]**&#x200B;標籤新增至範本和行銷活動的詳細資訊，以便選取相關預算。

  ![](assets/s_ncs_user_op_template_activate_7.png)

## 屬性和執行 {#general-configuration}

### 範本屬性 {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

建立行銷活動範本時，需要輸入下列資訊：

* 輸入範本的&#x200B;**標籤**：依預設，此標籤會指派給透過此範本建立的所有行銷活動。
* 從下拉式清單中選取行銷活動&#x200B;**性質**。 此清單中可用的值是儲存在&#x200B;**[!UICONTROL natureOp]**&#x200B;列舉中的值。

  >[!NOTE]
  >
  >在&#x200B;**Adobe Campaign v8 （主控台）檔案**&#x200B;中進一步瞭解如何[使用分項清單](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}。

* 選取行銷活動&#x200B;**的**&#x200B;型別：唯一、循環或定期。 依預設，行銷活動範本適用於不重複行銷活動。 在[此區段](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)中詳細說明週期性行銷活動和週期性行銷活動。
* 指定行銷活動的持續時間，即行銷活動將發生的天數。 根據此範本建立行銷活動時，會自動填入行銷活動的開始和結束日期。

  如果行銷活動為週期性，您必須直接在範本中指定行銷活動開始和結束日期。

* 指定範本的&#x200B;**相關方案**：基於此範本的行銷活動將連結至選取的方案。

### 範本執行引數 {#template-execution-parameters}

**[!UICONTROL Advanced campaign settings...]**&#x200B;連結可讓您設定範本的進階選項，以處理傳遞目標（控制組、種子地址等）以及行銷活動測量和工作流程執行的設定。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 追蹤行銷活動執行{#campaign-reverse-scheduling}

您可以建立行銷活動的排程並追蹤成績，例如，為特定日期準備事件排程。 行銷活動範本現在可讓您根據行銷活動的結束日期計算任務的開始日期。

在工作設定方塊中，移至&#x200B;**[!UICONTROL Implementation schedule]**&#x200B;區域並核取&#x200B;**[!UICONTROL The start date is calculated based on the campaign end date]**&#x200B;方塊。 （在此，「開始日期」是任務的開始日期）。 移至&#x200B;**[!UICONTROL Start]**&#x200B;欄位並輸入間隔：任務將在行銷活動結束日期之前很久開始。 如果您輸入的期間長於促銷活動設為最後的時段，則任務會在促銷活動之前開始。

![](assets/mrm_task_in_template_start_date.png)

使用此範本建立行銷活動時，會自動計算任務開始日期。 不過，您之後一律可以加以變更。
