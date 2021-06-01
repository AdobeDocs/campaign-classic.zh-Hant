---
product: campaign
title: 個人化欄位
description: 個人化欄位
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 8%

---

# 個人化欄位{#personalization-fields}

個人化欄位係用於傳遞訊息內容的第一層級個人化。您在主要內容插入的欄位，將顯示從選取的資料來源插入資料的位置。

例如，具有&#x200B;**&lt;%= recipient.LastName %>**&#x200B;語法的個人化欄位會告訴Adobe Campaign將收件者的名稱插入資料庫（收件者表格）。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#personalization-fields-video)

>[!CAUTION]
>
>個人化欄位內容不能超過1024個字元。

## 資料源{#data-sources}

根據選取的傳送模式，個人化欄位可能來自兩種資料來源：

* Adobe Campaign資料庫是資料來源。 這是最常見的案例，例如「收件者個人化欄位」。 這些是收件者表格中定義的所有欄位，無論是標準欄位(通常：姓氏、名字、地址、城鎮、出生日期等) 或使用者定義的欄位。
* 外部檔案是資料來源。 這些是檔案欄中定義的所有欄位，使用外部檔案中找到的資料在傳送期間顯示為輸入。

>[!NOTE]
>
>Adobe Campaign個人化標籤的格式一律為&#x200B;**&lt;%=table.field%>**。

## 插入個人化欄位 {#inserting-a-personalization-field}

若要插入個人化欄位，請按一下可從任何標題、主旨或訊息內文編輯欄位存取的下拉式圖示。

![](assets/s_ncs_user_add_custom_field.png)

選取資料來源（收件者欄位或檔案欄位）後，此插入會採用命令的形式，此命令將由Adobe Campaign解譯，並由指定收件者的欄位值取代。 然後，您就可以在&#x200B;**[!UICONTROL Preview]**&#x200B;標籤中查看物理更換。

## 個人化欄位範例{#personalization-fields-example}

我們會建立電子郵件，先插入收件者姓名，然後在訊息內文中新增設定檔建立日期。 操作步驟：

1. 建立新傳送或開啟現有的電子郵件類型傳送。
1. 在傳遞精靈中，按一下&#x200B;**[!UICONTROL Subject]**&#x200B;編輯訊息的主旨並輸入主旨。
1. 輸入&quot; **[!UICONTROL Special offer for]** &quot;並使用工具列中的按鈕插入個人化欄位。 選取 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重複此操作以插入收件者的名稱。 在所有個人化欄位之間插入空格。
1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行驗證。
1. 在訊息內文中插入個人化。 要執行此操作，請按一下訊息內容中的，然後按一下欄位插入按鈕。
1. 選取 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 選擇要顯示的資訊欄位，然後按一下&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤以檢視個人化結果。 您必須選取收件者才能顯示該收件者的訊息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >當傳送屬於工作流程時，您可以使用暫時工作流程表格中的資料。 此資料會分組在&#x200B;**[!UICONTROL Target extension]**&#x200B;功能表中。 如需詳細資訊，請參閱[本章節](../../workflow/using/data-life-cycle.md#target-data)。

## 最佳化個人化{#optimizing-personalization}

您可以使用專用選項來最佳化個人化：**[!UICONTROL Prepare the personalization data with a workflow]**，可在傳送屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤中使用。 如需分析傳送的詳細資訊，請參閱[此區段](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在傳遞分析期間，此選項會自動建立並執行工作流程，將連結至目標的所有資料儲存在臨時表格中，包括來自FDA中連結之表格的資料。

核取此選項可在處理大量資料時，尤其是當個人化資料來自外部表格（透過FDA）時，大幅改善傳送分析效能。 如需詳細資訊，請參閱[存取外部資料庫(FDA)](../../installation/using/about-fda.md)。

例如，如果您在訊息內容中使用大量個人化欄位和/或個人化區塊時傳送給大量收件者時發生效能問題，此選項可加速個人化的處理，進而加速訊息的傳送。

若要使用此選項，請遵循下列步驟：

1. 建立促銷活動. 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在促銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中，將&#x200B;**Query**&#x200B;活動新增至工作流程。 有關使用此活動的詳細資訊，請參閱[此部分](../../workflow/using/query.md)。
1. 將&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動新增至工作流程並開啟它。 有關使用此活動的詳細資訊，請參閱[此部分](../../workflow/using/delivery.md)。
1. 前往&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤，然後選取&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;選項。

   ![](assets/perso_optimization.png)

1. 設定傳送並啟動工作流程以啟動分析。

分析完成後，個人化資料會透過分析期間即時建立的臨時技術工作流程儲存在臨時表格中。

此工作流程在Adobe Campaign介面中看不到。 這只是快速儲存及處理個人化資料的技術手段。

分析完成後，轉到工作流&#x200B;**[!UICONTROL Properties]**&#x200B;並選擇&#x200B;**[!UICONTROL Variables]**&#x200B;頁簽。 您可以在此處查看臨時表的名稱，該表可用於進行SQL調用，以顯示它包含的ID。

![](assets/perso_optimization_temp_table.png)

## 超時個人化階段{#timing-out-personalization}

若要改善傳送保護，您可以為個人化階段設定逾時期間。

在&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤中，為&#x200B;**[!UICONTROL Maximum personalization run time]**&#x200B;選項選擇以秒為單位的最大值。

在預覽或傳送期間，如果個人化階段超過您在此欄位中設定的時間上限，程式會因錯誤訊息而中止，且傳送會失敗。

![](assets/perso_time-out.png)

預設值為5秒。

如果將此選項設為0，則個人化階段不會有時間限制。

## 教學課程影片{#personalization-fields-video}

了解如何將個人化欄位新增至主旨行，以及電子郵件傳送的內容。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

其他Campaign Classic操作說明影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
