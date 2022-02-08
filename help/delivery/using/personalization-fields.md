---
product: campaign
title: 個人化欄位
description: 瞭解如何使用個性化欄位
feature: Personalization
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 10%

---

# 個人化欄位{#personalization-fields}

![](../../assets/common.svg)

個人化欄位係用於傳遞訊息內容的第一層級個人化。您在主要內容插入的欄位，將顯示從選取的資料來源插入資料的位置。

例如，帶有 **&lt;%=收件人。姓氏%>** 語法告訴Adobe Campaign將收件人的名稱插入資料庫（收件人表）。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#personalization-fields-video)

>[!CAUTION]
>
>個性化欄位內容不能超過1024個字元。

## 資料源 {#data-sources}

根據所選的傳送模式，個性化欄位可以來自兩種類型的資料源：

* Adobe Campaign資料庫是資料源。 這是最常見的情況，例如「收件人個性化欄位」。 這些是收件人表中定義的所有欄位，無論是標準欄位(通常為：姓氏、名字、地址、城鎮、出生日期等) 或用戶定義的欄位。
* 外部檔案是資料源。 這些是檔案列中定義的所有欄位，這些欄位在使用外部檔案中找到的資料進行傳遞時顯示為輸入。

>[!NOTE]
>
>Adobe Campaign個性化標籤始終具有以下窗體 **&lt;%=table.field%>**。

## 插入個人化欄位 {#inserting-a-personalization-field}

要插入個性化欄位，請按一下可從任何標題、主題或消息正文編輯欄位訪問的下拉表徵圖。

![](assets/s_ncs_user_add_custom_field.png)

在選擇資料源（收件人欄位或檔案欄位）後，此插入採用命令的形式，該命令將由Adobe Campaign解釋，並替換為給定收件人的欄位值。 然後，可以在 **[!UICONTROL Preview]** 頁籤。

## 個性化欄位示例 {#personalization-fields-example}

我們將建立一封電子郵件，在此電子郵件中我們將首先插入收件人的姓名，然後在郵件正文中添加配置檔案建立日期。 操作步驟：

1. 建立新的傳遞或開啟現有電子郵件類型傳遞。
1. 在傳遞嚮導中，按一下 **[!UICONTROL Subject]** 編輯消息的主題並輸入主題。
1. 輸入「」 **[!UICONTROL Special offer for]** 」，然後使用工具欄中的按鈕插入個性化欄位。 選取 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重複此操作以插入收件人的名稱。 在所有個性化欄位之間插入空格。
1. 按一下 **[!UICONTROL OK]** 驗證。
1. 在消息正文中插入個性化設定。 為此，請按一下消息內容，然後按一下欄位插入按鈕。
1. 選取 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 選擇要顯示的資訊的欄位，然後按一下 **[!UICONTROL OK]**。

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 按一下 **[!UICONTROL Preview]** 頁籤。 必須選擇一個收件人以顯示該收件人的郵件。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >當傳遞是工作流的一部分時，您可以使用臨時工作流表中的資料。 此資料將分組到 **[!UICONTROL Target extension]** 的子菜單。 如需詳細資訊，請參閱[本章節](../../workflow/using/data-life-cycle.md#target-data)。

## 優化個性化 {#optimizing-personalization}

可以使用專用選項優化個性化： **[!UICONTROL Prepare the personalization data with a workflow]**，在 **[!UICONTROL Analysis]** 的子菜單。 有關分析交貨的詳細資訊，請參閱 [此部分](steps-validating-the-delivery.md#analyzing-the-delivery)。

在傳遞分析期間，此選項會自動建立並執行一個工作流，該工作流將連結到目標的所有資料儲存在臨時表中，包括FDA連結的表中的資料。

選中此選項可在處理大量資料時大大提高交付分析效能，特別是當個性化資料通過FDA從外部表格來時。 有關此的詳細資訊，請參閱 [訪問外部資料庫(FDA)](../../installation/using/about-fda.md)。

例如，如果您在郵件內容中使用大量個性化欄位和/或個性化塊時向大量收件人發送時遇到效能問題，則此選項可加快個性化處理，從而加快郵件的發送。

要使用此選項，請執行以下步驟：

1. 建立促銷活動. 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在 **[!UICONTROL Targeting and workflows]** 頁籤，添加 **查詢** 活動。 有關使用本練習的詳細資訊，請參閱 [此部分](../../workflow/using/query.md)。
1. 添加 **[!UICONTROL Email delivery]** 活動並將其開啟。 有關使用本練習的詳細資訊，請參閱 [此部分](../../workflow/using/delivery.md)。
1. 轉到 **[!UICONTROL Analysis]** 頁籤 **[!UICONTROL Delivery properties]** 的 **[!UICONTROL Prepare the personalization data with a workflow]** 的雙曲餘切值。

   ![](assets/perso_optimization.png)

1. 配置交付並啟動工作流以啟動分析。

分析完成後，個性化資料通過分析期間即時建立的臨時技術工作流儲存在臨時表中。

此工作流在Adobe Campaign介面中不可見。 它只是一種技術手段來快速儲存和處理個性化資料。

分析完成後，轉到工作流 **[!UICONTROL Properties]** 的 **[!UICONTROL Variables]** 頁籤。 在此，您可以看到用於進行SQL調用以顯示其包含的ID的臨時表的名稱。

![](assets/perso_optimization_temp_table.png)

## 超時個性化階段 {#timing-out-personalization}

要改進交付保護，您可以設定個性化階段的超時時間。

在 **[!UICONTROL Delivery]** 頁籤 **[!UICONTROL Delivery properties]**，為 **[!UICONTROL Maximum personalization run time]** 的雙曲餘切值。

在預覽或發送期間，如果個性化階段超過您在此欄位中設定的最長時間，則進程將中止，並顯示錯誤消息，傳遞將失敗。

![](assets/perso_time-out.png)

預設值為5秒。

如果將此選項設定為0，則個性化階段將沒有時間限制。

## 教程視頻 {#personalization-fields-video}

瞭解如何將個人化欄位新增至主旨行，以及電子郵件傳送的內容。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

可提供其他Campaign Classic操作視頻 [這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)。
