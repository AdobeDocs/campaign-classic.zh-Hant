---
title: 重複資料刪除
seo-title: 重複資料刪除
description: 重複資料刪除
seo-description: null
page-status-flag: never-activated
uuid: 90dee589-ac45-442e-89ef-1c14bb22200d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 83b915bd-7e23-41b5-9f9a-f7eb72026376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0d2270c9d980d963437f9bb5cf37795474d261d6
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# 重複資料刪除{#deduplication}

重複資料消除從入站活動的結果中刪除重複項。 可在電子郵件地址、電話號碼或其他欄位上執行重複資料刪除。

## 最佳作法 {#best-practices}

在重複資料消除期間，入站流將單獨處理。 例如，如果在查詢1的結果和查詢2的結果中都找到收件者A，則不會對它們進行重複資料消除。

此問題需解決如下：

* 建立 **Union** 活動以統一每個入站流。
* 在Union活 **動之後** ，建立重複數 **據消除活動** 。

![](assets/dedup_bonnepratique.png)

## 配置 {#configuration}

要配置重複資料消除，請輸入其標籤、方法和重複資料消除標準，以及與結果相關的選項。

按一下鏈 **[!UICONTROL Edit configuration...]** 接以定義重複資料消除模式。

![](assets/s_user_segmentation_dedup_param.png)

1. 目標選擇

   選擇此活動的目標類型（預設情況下，重複資料消除涉及收件人）和要使用的標準，即相同值允許您識別重複項的欄位： 電子郵件地址、行動電話或電話號碼、傳真號碼或直接郵件地址。

   ![](assets/s_user_segmentation_dedup_param2.png)

   >[!NOTE]
   >
   >如果您使用外部資料作為輸入（例如來自外部檔案），請務必選取選 **[!UICONTROL Temporary schema]** 項。
在下一步中，選 **[!UICONTROL Other]** 項可讓您選取要使用的准則或准則：

   ![](assets/s_user_segmentation_dedup_param3.png)

1. 重複資料消除方法

   從下拉清單中，選擇要使用的重複資料消除方法，並輸入要保留的重複數。

   ![](assets/s_user_segmentation_dedup_param4.png)

   可使用下列方法：

   * **[!UICONTROL Choose for me]**: 隨機選擇要從重複項中保留的記錄。
   * **[!UICONTROL Following a list of values]**: 可讓您定義一或多個欄位的值優先順序。 要定義值，請選擇一個欄位或建立表達式，然後將值添加到相應的表中。 若要定義新欄位，請按一 **[!UICONTROL Add]** 下值清單上方的按鈕。

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**: 這可讓您保留所選運算式值不為空的記錄作為優先順序。

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**: 可讓您使用指定運算式的最低（或最高）值來保存記錄。

      ![](assets/s_user_segmentation_dedup_param7.png)
   按一下 **[!UICONTROL Finish]** 以批准所選的重複資料消除方法。

   窗口的中部區域將匯總定義的配置。

   在活動編輯器窗口的下部，您可以修改圖形對象的出站轉換標籤，並輸入與活動結果關聯的段代碼。 此程式碼稍後可用作定位標準。

   ![](assets/s_user_segmentation_dedup_param8.png)

   如果您 **[!UICONTROL Generate complement]** 想利用剩餘人口，請勾選選項。 補碼由所有復本組成。 然後，活動中會新增額外的轉場，如下所示：

   ![](assets/s_user_segmentation_dedup_param9.png)

## 範例： 在傳送前識別重複項目 {#example--identify-the-duplicates-before-a-delivery}

在以下示例中，重複資料消除涉及三個查詢的聯合。

工作流程的目的是透過排除重複項目來定義傳送的目標，以避免多次傳送給相同的收件者。

標識的重複項還將整合到專用的重複項清單中，如有必要，可以重複使用。

![](assets/deduplication_example.png)

1. 新增並連結工作流程運作所需的各種活動，如上所示。

   此處使用union活動將三個查詢「統一」為單一轉換。 因此，重複資料刪除不能單獨用於每個查詢，而是用於整個查詢。 有關此主題的詳細資訊，請參閱最 [佳實務](#best-practices)。

1. 開啟重複資料消除活動，然後按一下 **[!UICONTROL Edit configuration...]** 連結以定義重複資料消除模式。
1. 在新窗口中，選擇 **[!UICONTROL Database schema]**。
1. 選取「 **收件者** 」作為定位和篩選維度。
1. 選取復本的ID欄位， **[!UICONTROL Email]** 將傳送內容只傳送一次至每個電子郵件地址，然後按一下 **[!UICONTROL Next]**。

   如果您希望將重複的ID建立在特定欄位上，請選 **[!UICONTROL Other]** 取以存取可用欄位清單。

1. 選擇只保留一個項目，當為多個收件者識別相同的電子郵件地址時。
1. 選擇重 **[!UICONTROL Choose for me]** 復資料消除模式，以便隨機選擇在發現重複資料時保存的記錄，然後按一下 **[!UICONTROL Finish]**。

當執行工作流程時，所有識別為重複項目的收件者都會從結果中排除（因此也會排除傳送），並新增至重複項清單。 此清單可能會再次使用，而不需要重新識別重複項目。

## 輸入參數 {#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這組三個值標識了重複資料消除產生的目標。 **[!UICONTROL tableName]** 是保存目標標識符的表的名稱， **[!UICONTROL schema]** 是人口（通常是nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素數。

與補體相關的過渡具有相同的參數。
