---
title: 透過工作流程整合選件
seo-title: 透過工作流程整合選件
description: 透過工作流程整合選件
seo-description: null
page-status-flag: never-activated
uuid: 57c4d4e0-6594-46f0-b9ce-2c689fb2eaa2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
discoiquuid: 6e27caea-1f1a-457d-bdec-1f93a12b01cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# 透過工作流程整合選件{#integrating-an-offer-via-a-workflow}

在傳送活動本身之外，數個工作流程活動可讓您定義選件的呈現方式：

* 傳送大綱
* 擴充
* 選件引擎
* 依儲存格列出的選件

## 傳送大綱 {#delivery-outline}

促銷活動工作流程中提供的傳送大綱活動，可讓您顯示目前促銷活動中傳送大綱中參考的選件。

1. 在工作流程中，新增傳送大綱活動之前，先新增傳送大綱活動。
1. 在傳送大綱活動中，指定您要使用的大綱。

   如需指定傳送外框的詳細資訊，請參閱「促銷活 [動- MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) 」指南。

1. 根據您的傳送完成可用欄位。
1. 可能有兩種情況：

   * 如果您想要呼叫選件引擎，請核取方 **[!UICONTROL Restrict the number of propositions selected]** 塊。 指定選件空間和將在傳送中呈現的主張數目。

      選件引擎會考量到選件權重和資格規則。

   * 如果您未勾選此方塊，傳送大綱中的所有選件都會顯示，而不會呼叫選件引擎。
   >[!NOTE]
   >
   >預覽會考量傳送中指定的選件數。 執行工作流時，會考慮到在傳送大綱中指定的數字。

   ![](assets/int_compo_offre_wf1.png)

## 擴充 {#enrichment}

擴充活動可讓您新增選件或連結至傳送收件者的選件。

>[!NOTE]
>
>有關擴充活動的詳細資訊，請參閱「工作流程」指南中的專 [用檔案](../../workflow/using/enrichment.md)。

例如，您可以在傳送前豐富收件者查詢的資料。

![](assets/int_enrichment_offer1.png)

指定選件主張的方法有兩種。

* 指定選件或選件引擎呼叫。
* 參考選件的連結。

### 指定選件或對選件引擎的呼叫 {#specifying-an-offer-or-a-call-to-the-offer-engine}

設定查詢後(請參閱「工作 [流程指南](../../workflow/using/query.md)」):

1. 新增並開啟擴充活動。
1. 在頁籤 **[!UICONTROL Enrichment]** 中，選擇 **[!UICONTROL Add data]**。
1. 在要 **[!UICONTROL An offer proposition]** 添加的資料類型中選擇。

   ![](assets/int_enrichment_offer2.png)

1. 指定要新增之提案的識別碼和標籤。
1. 指定選件選擇。 這有兩個可能的選項：

   * **[!UICONTROL Search for the best offer in a category]** :勾選此選項並指定選件引擎呼叫參數（選件空間、類別或主題、連絡日期、要保留的選件數）。 引擎會根據這些參數自動計算要新增的選件。 我們建議您完成 **[!UICONTROL Category]** 或欄 **[!UICONTROL Theme]** 位，而不是同時完成兩者。

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** :勾選此選項並指定選件空間、特定選件和連絡日期，以直接設定您要新增的選件，毋需呼叫選件引擎。

      ![](assets/int_enrichment_offer4.png)

1. 然後設定與您所選渠道對應的傳送活動。 如需詳細資訊，請參閱將選 [件提案插入傳送區段](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

   >[!NOTE]
   >
   >預覽可用的建議數取決於在濃縮活動中執行的配置，而不是直接在交付中執行的任何可能的配置。

### 參考選件的連結 {#referencing-a-link-to-an-offer}

您也可以參考擴充活動中選件的連結。

若要這麼做，請使用下列程式：

1. 在活 **[!UICONTROL Add data]** 動的標籤中選 **[!UICONTROL Enrichment]** 擇。
1. 在您選擇要添加的資料類型的窗口中，選擇 **[!UICONTROL A link]**。
1. 選擇要建立的連結類型及其目標。 在此情況下，目標是選件結構。

   ![](assets/int_enrichment_link1.png)

1. 指定擴充活動（在此收件者表格）中的傳入表格資料與選件表格之間的連結。 例如，您可以將選件代碼連結至收件者。

   ![](assets/int_enrichment_link2.png)

1. 然後設定與您所選渠道對應的傳送活動。 如需詳細資訊，請參閱將選 [件提案插入傳送區段](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

   >[!NOTE]
   >
   >預覽可用的建議數取決於交付中執行的配置。

### 儲存選件排名和權重 {#storing-offer-rankings-and-weights}

依預設，當使用 **擴充活動** 來提供選件時，其排名和權重不會儲存在命題表格中。

>[!NOTE]
>
>記住：依預 **[!UICONTROL Offer engine]** 設，活動會儲存此資訊。

但是，您可以按如下方式儲存此資訊：

1. 在查詢之後和傳送活動之前放置的擴充活動中，建立對選件引擎的呼叫。 請參閱「指 [定選件或對選件引擎的呼叫](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine) 」區段。
1. 在活動的主窗口中，選擇 **[!UICONTROL Edit additional data...]**。

   ![](assets/ita_enrichment_rankweight_1.png)

1. 新增 **[!UICONTROL @rank]** 排名和選件 **[!UICONTROL @weight]** 權重的欄。

   ![](assets/ita_enrichment_rankweight_2.png)

1. 確認您的新增功能並儲存您的工作流程。

傳送會自動儲存選件的排名和權重。 此資訊會顯示在傳送的標籤 **[!UICONTROL Offers]** 中。

## 選件引擎 {#offer-engine}

此活 **[!UICONTROL Offer engine]** 動也可讓您在傳送前指定對選件引擎的呼叫。

此活動與引擎呼叫的富集活動具有相同的原則，即在傳送之前，使用引擎計算的選件來富集傳入人口資料。

![](assets/int_offerengine_activity2.png)

設定查詢後(請參閱「工作 [流程指南](../../workflow/using/query.md)」):

1. 新增並開啟活 **[!UICONTROL Offer engine]** 動。
1. 填寫各種可用欄位，以指定對選件引擎參數（選件空間、類別或主題、連絡日期、要保留的選件數）的呼叫。 引擎會根據這些參數自動計算要新增的選件。

   >[!NOTE]
   >
   >警告：如果您使用本活動，則只會儲存傳送中使用的選件主張。

   ![](assets/int_offerengine_activity1.png)

1. 然後設定與您所選渠道對應的傳送活動。 如需詳細資訊，請參閱將選 [件提案插入傳送區段](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

## 依儲存格列出的選件 {#offers-by-cell}

此活 **[!UICONTROL Offers by cell]** 動可讓您將傳入人口（例如從查詢）分發到數個區段，並指定要針對每個區段顯示的選件。

若要這麼做，請使用下列程式：

1. 在您指 **[!UICONTROL Offers by cell]** 定目標人口後新增活動，然後開啟它。
1. 在標 **[!UICONTROL General]** 簽中，選取您要在其中呈現選件的選件空間。
1. 在標籤 **[!UICONTROL Cells]** 中，使用按鈕指定不同的子 **[!UICONTROL Add]** 集：

   * 使用可用的篩選和限制規則指定子集填入。
   * 然後選取您要呈現給子集的選件。 可用的選件是符合在上一步驟中選取之選件環境的選件。

      ![](assets/int_offer_per_cell1.png)

1. 然後設定與您所選渠道對應的傳送活動。 如需詳細資訊，請參閱將選 [件提案插入傳送區段](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

