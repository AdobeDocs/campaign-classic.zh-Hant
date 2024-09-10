---
product: campaign
title: 透過工作流程整合優惠方案
description: 透過工作流程整合優惠方案
feature: Interaction, Offers, Workflows
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 33d318f3-1eb4-4c74-8c20-8b9f0442c7c3
source-git-commit: de9ff0b50d819038c97e8515ddb7d6cfeb4547a1
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 1%

---

# 透過工作流程整合優惠方案{#integrating-an-offer-via-a-workflow}



在傳遞活動本身之外，有數個工作流程活動可讓您定義優惠方案的顯示方式：

* 傳遞大綱
* 擴充
* 優惠引擎
* 依儲存格列出的優惠

## 傳遞大綱 {#delivery-outline}

行銷活動工作流程中可用的傳遞大網活動，可讓您顯示目前進行中行銷活動之傳遞大網所參考的選件。

1. 在工作流程中，新增傳遞活動之前，請先新增傳遞大網活動。
1. 在傳遞大網活動中，指定您要使用的大網。

   如需指定傳遞大網的詳細資訊，請參閱[Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)指南。

1. 根據您的傳送完成可用的欄位。
1. 有兩種可能的情況：

   * 如果要呼叫優惠方案引擎，請核取&#x200B;**[!UICONTROL Restrict the number of propositions selected]**&#x200B;方塊。 指定優惠方案空間以及將在傳遞中顯示的建議數量。

     優惠方案引擎會考慮優惠方案權重和適用性規則。

   * 如果您未勾選此方塊，則傳遞大網中的所有優惠方案都會顯示，而不會呼叫優惠方案引擎。

   >[!NOTE]
   >
   >預覽會考量傳送中指定的優惠方案數量。 執行工作流程時，會考慮傳遞大網中指定的數字。

   ![](assets/int_compo_offre_wf1.png)

## 擴充 {#enrichment}

擴充活動可讓您將優惠或連結新增至傳遞收件者的優惠。

>[!NOTE]
>
>如需擴充活動的詳細資訊，請參閱[工作流程手冊](../../workflow/using/enrichment.md)中的專屬檔案。

例如，您可以在傳遞前擴充收件者查詢的資料。

![](assets/int_enrichment_offer1.png)

指定優惠方案主張有兩個方法。

* 指定優惠方案或優惠方案引擎呼叫。
* 參照優惠方案的連結。

### 指定優惠方案或呼叫優惠方案引擎 {#specifying-an-offer-or-a-call-to-the-offer-engine}

設定查詢之後（請參閱[工作流程手冊](../../workflow/using/query.md)）：

1. 新增並開啟擴充活動。
1. 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;索引標籤中，選取&#x200B;**[!UICONTROL Add data]**。
1. 在要新增的資料型別中選取&#x200B;**[!UICONTROL An offer proposition]**。

   ![](assets/int_enrichment_offer2.png)

1. 指定要新增之主張的識別碼和標籤。
1. 指定優惠方案選取專案。 對此有兩種可能的選項：

   * **[!UICONTROL Search for the best offer in a category]** ：核取此選項，並指定優惠方案引擎呼叫引數（優惠方案空間、類別或主題、聯絡日期、要保留的優惠方案數目）。 引擎將根據這些引數自動計算要新增的選件。 我們建議完成&#x200B;**[!UICONTROL Category]**&#x200B;或&#x200B;**[!UICONTROL Theme]**&#x200B;欄位，而不是同時完成兩者。

     ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** ：核取此選項，並指定優惠方案空間、特定優惠方案和聯絡人日期，以直接設定您要新增的優惠方案，而不呼叫優惠方案引擎。

     ![](assets/int_enrichment_offer4.png)

1. 然後，設定與您所選管道對應的傳送活動。 如需詳細資訊，請參閱[將優惠方案主張插入傳遞](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)區段。

   >[!NOTE]
   >
   >可供預覽的建議數量取決於擴充活動中執行的設定，而非直接在傳送中執行的任何可能設定。

### 參照優惠方案的連結 {#referencing-a-link-to-an-offer}

您也可以在擴充活動中參考優惠方案的連結。

要執行此操作，請使用下列程式：

1. 在活動的&#x200B;**[!UICONTROL Enrichment]**&#x200B;索引標籤中選取&#x200B;**[!UICONTROL Add data]**。
1. 在您選擇要新增的資料型別視窗中，選取&#x200B;**[!UICONTROL A link]**。
1. 選取您要建立的連結型別及其目標。 在此案例中，目標是選件結構描述。

   ![](assets/int_enrichment_link1.png)

1. 指定擴充活動（此處為收件者表格）中傳入表格資料與優惠方案表格之間的聯結。 例如，您可以將優惠代碼連結至收件者。

   ![](assets/int_enrichment_link2.png)

1. 然後，設定與您所選管道對應的傳送活動。 如需詳細資訊，請參閱[將優惠方案主張插入傳遞](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)區段。

   >[!NOTE]
   >
   >可供預覽的建議數量取決於傳遞中執行的設定。

### 儲存優惠排名和權重 {#storing-offer-rankings-and-weights}

根據預設，使用&#x200B;**擴充**&#x200B;活動傳遞優惠時，其排名和權重不會儲存在主張表格中。

>[!NOTE]
>
>記住： **[!UICONTROL Offer engine]**&#x200B;活動預設會儲存此資訊。

不過，您可以依照以下方式儲存此資訊：

1. 在查詢之後及傳遞活動之前的擴充活動中，建立對優惠方案引擎的呼叫。 請參閱[指定優惠或呼叫優惠引擎](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine)區段。
1. 在活動的主視窗中，選取&#x200B;**[!UICONTROL Edit additional data...]**。

   ![](assets/ita_enrichment_rankweight_1.png)

1. 新增排名的&#x200B;**[!UICONTROL @rank]**&#x200B;欄以及優惠權重的&#x200B;**[!UICONTROL @weight]**。

   ![](assets/ita_enrichment_rankweight_2.png)

1. 確認新增並儲存工作流程。

傳遞會自動儲存優惠方案的排名和權重。 此資訊會顯示在傳遞的&#x200B;**[!UICONTROL Offers]**&#x200B;標籤中。

## 優惠引擎 {#offer-engine}

**[!UICONTROL Offer engine]**&#x200B;活動也可讓您在傳遞前指定呼叫優惠方案引擎。

此活動的運作原則與引擎呼叫的擴充活動相同，也就是在傳送前，使用引擎計算的優惠擴充入站母體資料。

![](assets/int_offerengine_activity2.png)

設定查詢之後（請參閱[工作流程手冊](../../workflow/using/query.md)）：

1. 新增並開啟&#x200B;**[!UICONTROL Offer engine]**&#x200B;活動。
1. 完成各種可用欄位，以指定呼叫優惠方案引擎引數（優惠方案空間、類別或主題、聯絡日期、要保留的優惠方案數量）。 引擎將根據這些引數自動計算要新增的選件。

   >[!NOTE]
   >
   >警告：如果您使用此活動，則只會儲存傳送中使用的優惠方案主張。

   ![](assets/int_offerengine_activity1.png)

1. 然後，設定與您所選管道對應的傳送活動。 如需詳細資訊，請參閱[將優惠方案主張插入傳遞](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)區段。

## 依儲存格列出的優惠 {#offers-by-cell}

**[!UICONTROL Offers by cell]**&#x200B;活動可讓您將入站母體（例如從查詢）分配至數個區段，並指定要針對每個區段呈現的選件。

要執行此操作，請使用下列程式：

1. 在指定目標母體後，新增&#x200B;**[!UICONTROL Offers by cell]**&#x200B;活動，然後開啟它。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中，選取您要顯示優惠方案的優惠方案空間。
1. 在&#x200B;**[!UICONTROL Cells]**&#x200B;索引標籤中，使用&#x200B;**[!UICONTROL Add]**&#x200B;按鈕指定不同的子集：

   * 使用可用的篩選和限制規則指定子集母體。
   * 然後選取您要呈現給子集的選件。 可用的優惠方案是在上一步驟中選取的優惠方案環境中符合條件的優惠方案。

     ![](assets/int_offer_per_cell1.png)

1. 然後，設定與您所選管道對應的傳送活動。 如需詳細資訊，請參閱[將優惠方案主張插入傳遞](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)區段。
