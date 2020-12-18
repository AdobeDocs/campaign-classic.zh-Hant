---
solution: Campaign Classic
product: campaign
title: 個人化欄位
description: 個人化欄位
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 8%

---


# 個人化欄位{#personalization-fields}

個人化欄位係用於傳遞訊息內容的第一層級個人化。您在主要內容插入的欄位，將顯示從選取的資料來源插入資料的位置。

例如，具有&#x200B;**&lt;%= recipient.LastName %>**&#x200B;語法的個人化欄位會告訴Adobe Campaign將收件者名稱插入資料庫（收件者表格）。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#personalization-fields-video)

>[!CAUTION]
>
>個人化欄位內容不能超過1024個字元。

## 資料來源{#data-sources}

個人化欄位可以根據選取的傳送模式，來自兩種資料來源：

* Adobe Campaign資料庫是資料來源。 這是最常見的情況，例如「收件者個人化欄位」。 這些是在收件者表格中定義的所有欄位，不論是標準欄位(通常：姓氏、名字、地址、城鎮、出生日期等) 或使用者定義欄位。
* 外部檔案是資料源。 這些是檔案欄中定義的所有欄位，在傳送期間使用外部檔案中的資料顯示為輸入。

>[!NOTE]
>
>Adobe Campaign個人化標籤的格式一律為&#x200B;**&lt;%=table.field%>**。

## 插入個人化欄位 {#inserting-a-personalization-field}

若要插入個人化欄位，請按一下可從任何標題、主旨或訊息內文編輯欄位存取的下拉式圖示。

![](assets/s_ncs_user_add_custom_field.png)

在選取資料來源（收件者欄位或檔案欄位）後，此插入會採用命令的形式，由Adobe Campaign解釋，並由指定收件者的欄位值所取代。 然後，您可以在&#x200B;**[!UICONTROL Preview]**&#x200B;標籤中查看物理更換。

## 個人化欄位範例{#personalization-fields-example}

我們會建立電子郵件，我們會先插入收件者的名稱，然後在訊息正文中新增描述檔建立日期。 操作步驟：

1. 建立新的傳送，或開啟現有的電子郵件類型傳送。
1. 在傳送精靈中，按一下&#x200B;**[!UICONTROL Subject]**&#x200B;以編輯訊息的主旨並輸入主旨。
1. 輸入&quot; **[!UICONTROL Special offer for]** &quot;，然後使用工具列中的按鈕插入個人化欄位。 選取 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重複此操作以插入收件人的名稱。 在所有個人化欄位之間插入空格。
1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行驗證。
1. 將個人化插入訊息內文。 若要這麼做，請按一下訊息內容中的，然後按一下欄位插入按鈕。
1. 選取 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 選擇要顯示的資訊欄位，然後按一下&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤以檢視個人化結果。 您必須選擇收件者，才能顯示該收件者的訊息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >當傳送是工作流程的一部分時，您可以使用臨時工作流程表格中的資料。 此資料在&#x200B;**[!UICONTROL Target extension]**&#x200B;功能表中分組。 如需詳細資訊，請參閱[本章節](../../workflow/using/data-life-cycle.md#target-data)。

## 最佳化個人化{#optimizing-personalization}

您可以使用專屬選項來最佳化個人化：**[!UICONTROL Prepare the personalization data with a workflow]**，可在傳送屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤中取得。 如需分析傳送的詳細資訊，請參閱[本節](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在傳送分析期間，此選項會自動建立並執行將所有連結至目標的資料儲存在暫存表格中的工作流程，包括FDA中連結之表格的資料。

在處理大量資料時，檢查此選項可大幅改善傳送分析效能，尤其是當個人化資料來自透過FDA的外部表格時。 有關詳細資訊，請參見[訪問外部資料庫(FDA)](../../installation/using/about-fda.md)。

例如，如果您在傳送訊息給大量收件者時，在訊息內容中使用許多個人化欄位和／或個人化區塊，遇到效能問題，這個選項可加速個人化的處理，進而加速訊息的傳送。

若要使用此選項，請遵循下列步驟：

1. 建立促銷活動. 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在促銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中，將&#x200B;**Query**&#x200B;活動新增至工作流程。 有關使用本練習的詳細資訊，請參閱[本節](../../workflow/using/query.md)。
1. 新增&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動至工作流程並開啟它。 有關使用本練習的詳細資訊，請參閱[本節](../../workflow/using/delivery.md)。
1. 轉到&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Analysis]**&#x200B;頁籤，然後選擇&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;選項。

   ![](assets/perso_optimization.png)

1. 設定傳送並啟動工作流程以啟動分析。

分析完成後，個人化資料會透過分析期間即時建立的臨時技術工作流程，儲存在臨時表格中。

Adobe Campaign介面中不會顯示此工作流程。 它只是一種技術手段，可快速儲存和處理個人化資料。

分析完成後，轉至工作流&#x200B;**[!UICONTROL Properties]**&#x200B;並選擇&#x200B;**[!UICONTROL Variables]**&#x200B;頁籤。 您可以看到臨時表的名稱，該臨時表可用於進行SQL調用，以顯示它包含的ID。

![](assets/perso_optimization_temp_table.png)

## 個人化階段{#timing-out-personalization}逾時

若要改善傳送保護，您可以設定個人化階段的逾時期。

在&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤中，為&#x200B;**[!UICONTROL Maximum personalization run time]**&#x200B;選項選擇以秒為單位的最大值。

在預覽或傳送期間，如果個人化階段超過您在此欄位中設定的最長時間，則會中止程式並顯示錯誤訊息，而傳送將會失敗。

![](assets/perso_time-out.png)

預設值為5秒。

如果您將此選項設為0，個人化階段將不會有時間限制。

## 教學課程影片{#personalization-fields-video}

瞭解如何將個人化欄位新增至主旨行，以及電子郵件傳送的內容。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

其他Campaign Classic操作視訊可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
