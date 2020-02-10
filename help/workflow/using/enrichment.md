---
title: 擴充
seo-title: 擴充
description: 擴充
seo-description: null
page-status-flag: never-activated
uuid: 8dad57b7-fa08-48ee-990c-f9f0bb312d1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: b7ff47e1-ef12-4f04-afff-1a6c01d7701f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 擴充{#enrichment}

此活 **[!UICONTROL Enrichment]** 動可讓您將資訊新增至描述檔清單，並連結至現有表格（建立新的連結）。 還可以定義資料庫中具有配置檔案的協調標準。

![](assets/enrichment_design.png)

## 定義 {#definitions}

若要使用擴充活動，您必須熟悉新增資料時的各種可用選項。

![](assets/enrichment_edit.png)

此選 **[!UICONTROL Data linked to the filtering dimension]** 項可讓您存取：

* 篩選維度的資料：對工作表資料的訪問
* 連結至篩選維度的資料：對連結至工作表的資料的訪問

![](assets/wf_enrich_linkoptions.png)

選 **[!UICONTROL A link]** 項可讓您在資料庫的任何表上建立聯接。

![](assets/wf_enrich_linkstype.png)

連結有四種類型：

* **[!UICONTROL Define a collection]**:可讓您定義表格之間具有1-N基數的連結。
* **[!UICONTROL Define a link whose target is still available]**:可讓您定義表格間具有1-1基數的連結。 連接條件必須由目標表中的單個記錄定義。
* **[!UICONTROL Define a link whose target does not necessarily exist in the base]**:可讓您定義表格間具有0-1基數的連結。 連接條件必須由0或1（最大值）定義記錄在目標表格中。

   此選項在標籤中 **[!UICONTROL Simple Join]** 設定，可透過活動 **[!UICONTROL Edit additional data]** 連結存 **[!UICONTROL Enrichment]** 取。

* **[!UICONTROL Define a link by searching for a reference among several options]**:此類型的連結定義對唯一記錄的協調。 Adobe Campaign會在目標表格中新增外鍵，以儲存對唯一記錄的參考，以建立指向目標表格的連結。

   此選項在標籤中 **[!UICONTROL Reconciliation and deduplication]** 設定，可透過活動 **[!UICONTROL Edit additional data]** 連結存 **[!UICONTROL Enrichment]** 取。

「豐 [富資料](../../workflow/using/enriching-data.md) 」和「創 [](../../workflow/using/creating-a-summary-list.md) 建概要清單」使用案例詳細說明了Enrichment活動在其上下文中的操作。

## 添加資訊 {#adding-information}

使用活 **[!UICONTROL Enrichment]** 動將列添加到工作表：此活動可用作查詢活動的補充。

其他列的配置在添加資料中 [有詳細說明](../../workflow/using/query.md#adding-data)。

此欄 **[!UICONTROL Primary set]** 位可讓您選取傳入的轉場：豐富了本活動工作台的資料。

按一下 **[!UICONTROL Add data]** 連結，並選取要新增的資料類型。 提供的資料類型清單取決於平台上安裝的模組和選項。 在最小的設定中，您隨時可以新增連結至篩選維度和連結的資料。

![](assets/enrichment_edit.png)

在以下範例中，對外轉場將豐富目標描述檔的年齡資訊。

![](assets/enrichment_add_data.png)

按一下右鍵濃縮活動的入站轉換，在濃縮階段之前查看資料。

![](assets/enrichment_content_before.png)

工作台包含以下資料和相關模式：

![](assets/enrichment_content_before_a.png)

在濃縮階段輸出中重複此操作。

![](assets/enrichment_content_after.png)

您可以看到已新增與描述檔年齡相關的資料：

![](assets/enrichment_content_after_a.png)

匹配模式也已豐富。

## 管理其他資料 {#managing-additional-data}

如果您 **[!UICONTROL Keep all additional data from the main set]** 不想保留先前定義的其他資料，請取消選取選項。 在這種情況下，只有在富集活動中選擇的附加列才會添加到傳出工作表。 不會儲存新增至上游活動的其他資訊。

![](assets/enrichment_edit_without_additional.png)

富集階段輸出的資料和模式如下：

![](assets/enrichment_content_after_without_additional.png)

## 建立連結 {#creating-a-link}

您可以使用擴充活動來建立工作資料與Adobe Campaign資料庫之間的連結：這將是傳入資料之間工作流程的本機連結。

例如，如果您載入包含收件者帳戶號碼、國家／地區和電子郵件的檔案資料，則必須建立國家／地區表格連結，才能在其個人檔案中更新此資訊。

若要這麼做，請套用下列步驟：

1. 收集並載入下列檔案類型：

   ```
   Account number;Country;Email
   18D65;FRANCE;agnes@gmail.com
   243PP;RUSSIA;paul@gmail.com
   55H87;CROATIA;dave@gmail.com
   56U81;USA;susan@gmail.com
   853PI;ITALY;anna@gmail.com
   890LP;FRANCE;robert@gmail.com
   83TY2;SWITZERLAND;mike@gmail.com
   ```

1. **編輯擴充活動，然後按一**&#x200B;下新增資料……連結以建立與「國家／地區」(Country)表的連接。

   ![](assets/enrichment_edit_after_file_box.png)

1. 選取選 **[!UICONTROL Link definition]** 項，然後按一下 **[!UICONTROL Next]** 按鈕。 指定要建立的連結類型。 在此示例中，我們希望將檔案收件人的國家與資料庫專用表中可用國家清單中的國家協調起來。 選擇選 **[!UICONTROL Define a link by searching for a reference among several options]** 項。 在欄位中選取國家／地區 **[!UICONTROL Target schema]** 表格。

   ![](assets/enrichment_add_a_link_select_option4.png)

1. 最後，選擇欄位，該欄位將允許您將源檔案值連結到資料庫中的值。

   ![](assets/enrichment_add_a_link_select_join.png)

在此擴充活動的輸出中，臨時模式將包含指向國家表的連結：

![](assets/enrichment_external_link_schema.png)

## 資料協調 {#data-reconciliation}

可使用擴充活動來設定資料協調，包括資料載入資料庫後。 在這種情況下，標 **[!UICONTROL Reconciliation]** 簽可讓您定義Adobe Campaign資料庫中的資料與工作表中資料之間的連結。

選擇 **[!UICONTROL Identify the targeting document based on work data]** 選項，指定要建立連結的方案，並定義連接條件：若要這麼做，請選取工作資料(**[!UICONTROL Source expression]**)和定位維度(**[!UICONTROL Destination expression]**)中要調節的欄位。

您可以使用一或多個協調標準。

![](assets/enrichment_reconciliations_tab_01.png)

如果指定了多個連接條件，則必須驗證這些條件ALL，以便將資料連結在一起。

## 插入選件提案 {#inserting-an-offer-proposition}

擴充活動可讓您新增選件或連結至傳送收件者的選件。

有關富集活動的詳細資訊，請參閱本 [節](../../workflow/using/enrichment.md)。

例如，您可以在傳送前豐富收件者查詢的資料。

![](assets/int_enrichment_offer1.png)

設定查詢後(請參閱本 [節](../../workflow/using/query.md)):

1. 新增並開啟擴充活動。
1. 在頁籤 **[!UICONTROL Enrichment]** 中，選擇 **[!UICONTROL Add data]**。
1. 在要 **[!UICONTROL An offer proposition]** 添加的資料類型中選擇。

   ![](assets/int_enrichment_offer2.png)

1. 指定要新增之提案的識別碼和標籤。
1. 指定選件選擇。 這有兩個可能的選項：

   * **[!UICONTROL Search for the best offer in a category]**:勾選此選項並指定選件引擎呼叫參數（選件空間、類別或主題、連絡日期、要保留的選件數）。 引擎會根據這些參數自動計算要新增的選件。 我們建議您完成 **[!UICONTROL Category]** 或欄 **[!UICONTROL Theme]** 位，而不是同時完成兩者。

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]**:勾選此選項並指定選件空間、特定選件和連絡日期，以直接設定您要新增的選件，毋需呼叫選件引擎。

      ![](assets/int_enrichment_offer4.png)

1. 然後設定與您所選渠道對應的傳送活動。 請參閱 [跨通道傳送](../../workflow/using/cross-channel-deliveries.md)。

   預覽可用的建議數取決於在濃縮活動中執行的配置，而不是直接在交付中執行的任何可能的配置。

若要指定選件主張，您也可以選擇參考選件的連結。 如需詳細資訊，請參閱下列章節參 [考選件的連結](#referencing-a-link-to-an-offer)。

## 參考選件的連結 {#referencing-a-link-to-an-offer}

您也可以參考擴充活動中選件的連結。

操作步驟：

1. 在活 **[!UICONTROL Add data]** 動的標籤中選 **[!UICONTROL Enrichment]** 擇。
1. 在您選擇要添加的資料類型的窗口中，選擇 **[!UICONTROL A link]**。
1. 選擇要建立的連結類型及其目標。 在此情況下，目標是選件結構。

   ![](assets/int_enrichment_link1.png)

1. 指定擴充活動（在此收件者表格）中的傳入表格資料與選件表格之間的連結。 例如，您可以將選件代碼連結至收件者。

   ![](assets/int_enrichment_link2.png)

1. 然後設定與您所選渠道對應的傳送活動。 請參閱 [跨通道傳送](../../workflow/using/cross-channel-deliveries.md)。

   >[!NOTE]
   >
   >預覽可用的建議數取決於交付中執行的配置。

## 儲存選件排名和權重 {#storing-offer-rankings-and-weights}

依預設，當使用 **擴充活動** 來提供選件時，其排名和權重不會儲存在命題表格中。

依預 **[!UICONTROL Offer engine]** 設，活動會儲存此資訊。

但是，您可以按如下方式儲存此資訊：

1. 在查詢之後和傳送活動之前放置的擴充活動中，建立對選件引擎的呼叫。 請參閱本 [節](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine)。
1. 在活動的主窗口中，選擇 **[!UICONTROL Edit additional data...]**。

   ![](assets/ita_enrichment_rankweight_1.png)

1. 新增 **[!UICONTROL @rank]** 排名和選件 **[!UICONTROL @weight]** 權重的欄。

   ![](assets/ita_enrichment_rankweight_2.png)

1. 確認您的新增功能並儲存您的工作流程。

傳送會自動儲存選件的排名和權重。 此資訊會顯示在傳送的標籤 **[!UICONTROL Offers]** 中。
