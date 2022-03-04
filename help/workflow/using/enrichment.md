---
product: campaign
title: 擴充
description: 瞭解有關「富集」工作流活動的詳細資訊
feature: Workflows, Enrichment Activity, Targeting Activity
exl-id: 4c7bc0f3-5877-47dc-bd72-dc94fb7bd479
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 2%

---

# 擴充{#enrichment}

![](../../assets/common.svg)

The **[!UICONTROL Enrichment]** activity lets you add information to a profile list and links to an existing table (create a new join). 還可以定義資料庫中具有配置檔案的協調條件。

![](assets/enrichment_design.png)

## 定義 {#definitions}

要使用富集活動，您需要熟悉添加資料時可用的各種選項。

![](assets/enrichment_edit.png)

的 **[!UICONTROL Data linked to the filtering dimension]** 選項，您可以訪問：

* 篩選維的資料：對工作表資料的訪問
* 連結到篩選維的資料：對連結到工作表的資料的訪問

![](assets/wf_enrich_linkoptions.png)

的 **[!UICONTROL A link]** 選項，可在資料庫的任何表上建立聯接。

![](assets/wf_enrich_linkstype.png)

有四種類型的連結：

* **[!UICONTROL Define a collection]**: lets you define a link with a 1-N cardinality between the tables.
* **[!UICONTROL Define a link whose target is still available]**: lets you define a link with a 1-1 cardinality between tables. 連接條件必須由目標表中的單個記錄定義。
* **[!UICONTROL Define a link whose target does not necessarily exist in the base]**:用於定義表之間具有0-1基數的連結。 連接條件必須由0或1（最大值）定義 在目標表中記錄。

   在 **[!UICONTROL Simple Join]** 可通過 **[!UICONTROL Edit additional data]** 連結 **[!UICONTROL Enrichment]** 的子菜單。

* **[!UICONTROL Define a link by searching for a reference among several options]**:此類型的連結定義對唯一記錄的協調。 Adobe Campaign creates a link to a target table by adding a foreign key in the target table for storing a reference to the unique record.

   在 **[!UICONTROL Reconciliation and deduplication]** 可通過 **[!UICONTROL Edit additional data]** 連結 **[!UICONTROL Enrichment]** 的子菜單。

以下各節還提供了詳細說明富集活動在其上下文中操作的使用案例：

* [使用自訂日期欄位擴充電子郵件](email-enrichment-with-custom-date-fields.md).
* [豐富資料](enriching-data.md)
* [建立摘要清單](creating-a-summary-list.md)

## 添加資訊 {#adding-information}

使用 **[!UICONTROL Enrichment]** 向工作表中添加列的活動：此活動可用作查詢活動的補充。

其他列的配置詳見 [添加資料](query.md#adding-data)。

的 **[!UICONTROL Primary set]** 欄位中，您可以選擇入站轉換：將豐富此活動工作台的資料。

按一下 **[!UICONTROL Add data]** 連結並選擇要添加的資料類型。 提供的資料類型清單取決於平台上安裝的模組和選項。 在最小配置中，始終可以添加連結到篩選維和連結的資料。

![](assets/enrichment_edit.png)

在以下示例中，將使用目標配置檔案的年齡資訊來豐富出站轉換。

![](assets/enrichment_add_data.png)

按一下右鍵濃縮活動的入站轉換，以查看濃縮階段之前的資料。

![](assets/enrichment_content_before.png)

工作表包含以下資料和關聯的架構：

![](assets/enrichment_content_before_a.png)

在富集階段輸出中重複此操作。

![](assets/enrichment_content_after.png)

您可以看到，已添加了與配置檔案使用期限相關的資料：

![](assets/enrichment_content_after_a.png)

還豐富了匹配架構。

## Managing additional data {#managing-additional-data}

取消選擇 **[!UICONTROL Keep all additional data from the main set]** 的子菜單。 在這種情況下，只有在富集活動中選擇的附加列才會添加到傳出工作表中。 將不保存添加到上游活動的附加資訊。

![](assets/enrichment_edit_without_additional.png)

濃縮階段輸出的資料和模式如下：

![](assets/enrichment_content_after_without_additional.png)

## 建立連結 {#creating-a-link}

You can use the enrichment activity to create a link between the working data and the Adobe Campaign database: this will be a local link to the workflow between the inbound data.

For example, if you load data of a file which contains the account number, country and email of recipients, you will have to create a link towards the country table in order to update this information in their profiles.

若要這麼做，請套用下列步驟：

1. 收集並載入以下類型的檔案：

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

1. 編輯富集活動，然後按一下 **添加資料……** 連結以建立與Country表的聯接。

   ![](assets/enrichment_edit_after_file_box.png)

1. Select the **[!UICONTROL Link definition]** option and click the **[!UICONTROL Next]** button. 指定要建立的連結的類型。 In this example, we want to reconcile the file recipient&#39;s country with a country in the list of available countries in the dedicated table of the database. 選取 **[!UICONTROL Define a link by searching for a reference among several options]** 選項。Select the country table in the **[!UICONTROL Target schema]** field.

   ![](assets/enrichment_add_a_link_select_option4.png)

1. 最後，選擇允許將源檔案值連結到資料庫中的值的欄位。

   ![](assets/enrichment_add_a_link_select_join.png)

在此富集活動的輸出處，臨時架構將包含到國家/地區表的連結：

![](assets/enrichment_external_link_schema.png)

## 資料協調 {#data-reconciliation}

該富集活動可用於配置資料協調，包括在資料載入到資料庫中之後。 在這個例子中， **[!UICONTROL Reconciliation]** 頁籤，用於定義Adobe Campaign資料庫中的資料與工作表中的資料之間的連結。

Select the **[!UICONTROL Identify the targeting document based on work data]** option, specify the schema you want to create a link to and define the joining conditions: to do this, select the fields to be reconciled in the work data (**[!UICONTROL Source expression]**) and in the targeting dimension (**[!UICONTROL Destination expression]**).

可以使用一個或多個協調條件。

![](assets/enrichment_reconciliations_tab_01.png)

如果指定了多個連接條件，則必須驗證這些條件ALL，以便將資料連結在一起。

## 插入優惠建議 {#inserting-an-offer-proposition}

The enrichment activity lets you add offers or links to offers for delivery recipients.

有關濃縮活動的詳細資訊，請參閱此 [節](enrichment.md)。

例如，您可以在傳遞之前為收件人查詢豐富資料。

![](assets/int_enrichment_offer1.png)

配置查詢後（請參閱此） [節](query.md)):

1. 添加並開啟富集活動。
1. 在 **[!UICONTROL Enrichment]** 索引標籤中，選取 **[!UICONTROL Add data]**。
1. 選擇 **[!UICONTROL An offer proposition]** 中。

   ![](assets/int_enrichment_offer2.png)

1. Specify an identifier as well as a label for the proposition that will be added.
1. 指定聘用選擇。 這有兩種可能的選擇：

   * **[!UICONTROL Search for the best offer in a category]**:選中此選項並指定聘用引擎呼叫參數（聘用空間、類別或主題、聯繫日期、要保留的聘用數）。 引擎將根據這些參數自動計算要添加的報價。 我們建議完成 **[!UICONTROL Category]** 或 **[!UICONTROL Theme]** 欄位，而不是同時執行。

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]**:選中此選項並指定聘用空間、特定聘用和聯繫日期，以直接配置您要添加的聘用，而無需調用聘用引擎。

      ![](assets/int_enrichment_offer4.png)

1. 然後配置與所選渠道對應的傳遞活動。 請參閱 [跨渠道交付](cross-channel-deliveries.md)。

   The number of propositions available for the preview depends on the configuration carried out in the enrichment activity rather than any possible configuration carried out directly in the delivery.

To specify offer propositions, you can also choose to reference a link to an offer. 有關詳細資訊，請參閱以下部分 [引用與優惠的連結](#referencing-a-link-to-an-offer)。

## Referencing a link to an offer {#referencing-a-link-to-an-offer}

您還可以引用富集活動中提供的連結。

操作步驟：

1. Select **[!UICONTROL Add data]** in the activity&#39;s **[!UICONTROL Enrichment]** tab.
1. 在選擇要添加的資料類型的窗口中，選擇 **[!UICONTROL A link]**。
1. 選擇要建立的連結類型及其目標。 在這種情況下，目標是提供方案。

   ![](assets/int_enrichment_link1.png)

1. 指定富集活動（此處為收件人表）中入站表資料與聘用表之間的聯接。 For example, you can link an offer code to a recipient.

   ![](assets/int_enrichment_link2.png)

1. 然後配置與所選渠道對應的傳遞活動。 請參閱 [跨渠道交付](cross-channel-deliveries.md)。

   >[!NOTE]
   >
   >可用於預覽的建議數取決於交付中執行的配置。

## 儲存服務排名和權重 {#storing-offer-rankings-and-weights}

預設情況下，當 **濃縮** 活動用於提供報價，其排名和權重不儲存在命題表中。

的 **[!UICONTROL Offer engine]** 預設情況下，活動會儲存此資訊。

但是，您可以按如下方式儲存此資訊：

1. 在查詢後和交貨活動前進行的富集活動中建立對供應引擎的調用。
1. 在活動的主窗口中，選擇 **[!UICONTROL Edit additional data...]**。

   ![](assets/ita_enrichment_rankweight_1.png)

1. 添加 **[!UICONTROL @rank]** 列 **[!UICONTROL @weight]** 來買份。

   ![](assets/ita_enrichment_rankweight_2.png)

1. 確認添加並保存工作流。

遞送自動儲存優惠的等級和權重。 此資訊在交貨的 **[!UICONTROL Offers]** 頁籤。
