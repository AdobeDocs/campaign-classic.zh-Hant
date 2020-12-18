---
solution: Campaign Classic
product: campaign
title: 一般匯入和匯出
description: 一般匯入和匯出
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 55%

---


# 一般匯入和匯出{#generic-imports-and-exports}

Adobe Campaign 提供了一個資料匯出模組，可以輕鬆提取客戶或潛在客戶清單 (例如，在定位操作之后)，然後他們將成為目標人群的一部分。

Adobe Campaign 還提供了一個匯入模組，可讓您使用外部檔案為資料庫提供資料。

>[!NOTE]
>
>導出和導入在通過工作流通過&#x200B;**[!UICONTROL Import]**&#x200B;和&#x200B;**[!UICONTROL Export]**&#x200B;活動執行的專用模板中配置。 它們可以根據時間表自動重複，例如多個資訊系統之間的自動化資料交換。如有必要，您可以透過Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**&#x200B;節點建立偶爾的匯入或匯出。

您可以：

* 建立匯入或匯出範本並對其進行配置 (參見下文)。
* 建立匯入或匯出：請參閱[匯出資料](../../platform/using/exporting-data.md)或[匯入資料](../../platform/using/importing-data.md)。
* 啟動導入或導出並監視其執行。 請參閱[執行追蹤](#execution-tracking)。

>[!CAUTION]
>
>Campaign 中的資料匯入應通過工作流程執行，以確保資料一致性並提高效率。有關詳細資訊，請參見[匯入資料](../../workflow/using/importing-data.md)、[匯入最佳實作](../../workflow/using/importing-data.md#best-practices-when-importing-data)和[匯入範本示例](../../workflow/using/importing-data.md#setting-up-a-recurring-import)部分。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

## 建立作業範本 {#creating-a-job-template}

匯入和匯出範本會儲存在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Resources > Templates > Job templates]**&#x200B;目錄中。

按照預設，此目錄中存在三個匯入範本和一個匯出範本。不得更改它們。您可以複製範本以建立自己的範本，或透過&#x200B;**[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**&#x200B;功能表建立新範本。

![](assets/s_ncs_user_export_wizard_template_create.png)

建立流程模板的過程顯示在[導出嚮導](../../platform/using/exporting-data.md#export-wizard)和[導入嚮導](../../platform/using/importing-data.md#import-wizard)中。

>[!NOTE]
>
>原生範本&#x200B;**[!UICONTROL Import denylist]**&#x200B;已設定為匯入已新增至denylist的電子郵件地址清單。
> 
>**[!UICONTROL New text import]**&#x200B;和&#x200B;**[!UICONTROL New text export]**&#x200B;範本可讓您從頭開始設定匯入或匯出。

## 建立新的匯入/匯出 {#creating-a-new-import-export}

配置範本後，可以在 Adobe Campaign 中的不同內容中啟動匯入和匯出操作。

所有這些操作都打開了[匯入](../../platform/using/importing-data.md)或[匯出](../../platform/using/exporting-data.md#export-wizard)精靈。

* 在Adobe Campaign工作區的&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;區段中，按一下&#x200B;**[!UICONTROL Jobs]**&#x200B;連結：這會帶您進入現有進出口清單。

   按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕，然後選擇要執行的作業類型。

   ![](assets/s_ncs_user_import_from_home.png)

* 您還可以從工作區的「監督」部分啟動匯入和匯出：兩個專用連結使您可以直接啟動匯入或匯出。

   ![](assets/s_ncs_user_import_from_production.png)

* 也可以從 Adobe Campaign Explorer 啟動匯入和匯出。

   要導出／導入資料，請按一下&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL New]**&#x200B;表徵圖，然後選擇&#x200B;**[!UICONTROL Export]**&#x200B;或&#x200B;**[!UICONTROL Import]**。 這將打開相應的精靈。

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## 執行追蹤 {#execution-tracking}

您可以在此編輯器的上半部分查看執行的追蹤。您可以通過匯入/匯出作業清單關閉匯出精靈並查看作業的執行情況。

![](assets/s_ncs_user_export_list_and_details.png)

* **[!UICONTROL Log]**&#x200B;標籤可讓您查看有關執行的日誌消息。
* **[!UICONTROL Rejects]**&#x200B;標籤包含拒絕的記錄。 請參閱[發生錯誤時的行為](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error)。

>[!NOTE]
>
>導入／導出作業狀態顯示在[作業狀態](../../platform/using/importing-data.md#job-statuses)中。

