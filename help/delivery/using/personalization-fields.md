---
product: campaign
title: 個人化欄位
description: 瞭解如何使用個人化欄位
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Personalization
role: User
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 9%

---

# 個人化欄位{#personalization-fields}

個人化欄位係用於傳遞訊息內容的第一層級個人化。您在主要內容插入的欄位，將顯示從選取的資料來源插入資料的位置。

例如，使用的個人化欄位 **&lt;%= recipient.LastName %>** 語法會指示Adobe Campaign將收件者名稱插入資料庫（收件者表格）。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#personalization-fields-video)

>[!CAUTION]
>
>個人化欄位內容不可超過1024個字元。

## 資料來源 {#data-sources}

根據所選的傳送模式，個人化欄位可能來自兩種型別的資料來源：

* Adobe Campaign資料庫是資料來源。 這是最常見的案例，例如「收件者個人化欄位」。 無論標準欄位（通常是：姓氏、名字、地址、城鎮、出生日期等），這些都是收件者表格中定義的所有欄位 或使用者定義的欄位。
* 外部檔案是資料來源。 這些是使用外部檔案中的資料進行傳遞期間，在檔案的欄中定義的所有欄位都會呈現為輸入。

>[!NOTE]
>
>Adobe Campaign個人化標籤一律會有以下形式 **&lt;%=table.field%>**.

## 插入個人化欄位 {#inserting-a-personalization-field}

若要插入個人化欄位，請按一下可從任何標題、主旨或郵件內文編輯欄位存取的下拉式圖示。

![](assets/s_ncs_user_add_custom_field.png)

在選擇資料來源（收件者欄位或檔案欄位）後，此插入會採用命令形式，由Adobe Campaign解譯並以指定收件者的欄位值取代。 然後您便可以在「 」中檢視實體更換 **[!UICONTROL Preview]** 標籤。

## 個人化欄位範例 {#personalization-fields-example}

我們會建立電子郵件，首先在其中插入收件者的名稱，然後在郵件內文中新增設定檔建立日期。 操作步驟：

1. 建立新傳遞或開啟現有的電子郵件型別傳遞。
1. 在傳遞精靈中，按一下 **[!UICONTROL Subject]** 編輯訊息的主旨並輸入主旨。
1. 輸入&quot; **[!UICONTROL Special offer for]** 」並使用工具列中的按鈕插入個人化欄位。 選取 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重複操作以插入收件者的名稱。 在所有個人化欄位之間插入空格。
1. 按一下 **[!UICONTROL OK]** 以進行驗證。
1. 在訊息本文中插入個人化。 若要這麼做，請按一下訊息內容中的，然後按一下欄位插入按鈕。
1. 選取 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 選取包含要顯示的資訊的欄位，然後按一下 **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 按一下 **[!UICONTROL Preview]** 標籤以檢視個人化結果。 您必須選取收件者以顯示該收件者的訊息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >當傳送屬於工作流程的一部分時，您可以使用暫時工作流程表格中的資料。 此資料會分組到 **[!UICONTROL Target extension]** 功能表。 如需詳細資訊，請參閱[本章節](../../workflow/using/data-life-cycle.md#target-data)。

## 最佳化個人化 {#optimizing-personalization}

您可以使用專用選項來最佳化個人化： **[!UICONTROL Prepare the personalization data with a workflow]**，可在 **[!UICONTROL Analysis]** 傳遞屬性的索引標籤。 如需分析傳遞的詳細資訊，請參閱 [本節](steps-validating-the-delivery.md#analyzing-the-delivery).

在傳遞分析期間，此選項會自動建立並執行工作流程，將所有連結至目標的資料儲存在臨時表格中，包括來自FDA連結表格的資料。

勾選此選項可大幅改善處理大量資料時的傳遞分析效能，尤其是當個人化資料來自透過FDA的外部表格時。 有關詳細資訊，請參閱 [存取外部資料庫(FDA)](../../installation/using/about-fda.md).

例如，如果您在傳送給大量收件者時，在訊息內容中使用大量個人化欄位和/或個人化區塊而遇到效能問題，此選項可以加速個人化的處理，並因此加速訊息的傳送。

若要使用此選項，請遵循下列步驟：

1. 建立行銷活動。 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在 **[!UICONTROL Targeting and workflows]** 索引標籤中，新增 **查詢** 活動至您的工作流程。 有關使用此活動的詳細資訊，請參閱 [本節](../../workflow/using/query.md).
1. 新增 **[!UICONTROL Email delivery]** 活動以開啟工作流程。 有關使用此活動的詳細資訊，請參閱 [本節](../../workflow/using/delivery.md).
1. 前往 **[!UICONTROL Analysis]** 的標籤 **[!UICONTROL Delivery properties]** 並選取 **[!UICONTROL Prepare the personalization data with a workflow]** 選項。

   ![](assets/perso_optimization.png)

1. 設定傳送並啟動工作流程以啟動分析。

分析完成後，個人化資料會透過分析期間即時建立的臨時技術工作流程，儲存在臨時表格中。

Adobe Campaign介面中看不到此工作流程。 其目的僅在於成為快速儲存和處理個人化資料的技術方法。

分析完成後，前往工作流程 **[!UICONTROL Properties]** 並選取 **[!UICONTROL Variables]** 標籤。 您可以在此看到可用來進行SQL呼叫以顯示其包含之ID的暫存表格名稱。

![](assets/perso_optimization_temp_table.png)

## 個人化階段逾時 {#timing-out-personalization}

若要改善傳送保護，您可以設定個人化階段的逾時期間。

在 **[!UICONTROL Delivery]** 的標籤 **[!UICONTROL Delivery properties]**，選取最大值（以秒為單位） **[!UICONTROL Maximum personalization run time]** 選項。

在預覽或傳送期間，如果個人化階段超過您在此欄位中設定的最大時間，流程將中止，並出現錯誤訊息，傳送將失敗。

![](assets/perso_time-out.png)

預設值為5秒。

如果您將此選項設為0，個人化階段將沒有時間限制。

## 教學課程影片 {#personalization-fields-video}

瞭解如何將個人化欄位新增至主旨行，以及電子郵件傳送的內容。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

提供其他Campaign Classic操作影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
