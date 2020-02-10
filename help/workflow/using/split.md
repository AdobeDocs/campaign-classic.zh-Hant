---
title: 分割
seo-title: 分割
description: 分割
seo-description: null
page-status-flag: never-activated
uuid: 00dc3436-e271-4512-8f29-71a55213afc3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 9eadfda0-0614-4e4e-aed0-26f0b9222fbd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 463d2d60e8776fc0414fdb8c91dbf257e119d823

---


# 分割{#split}

「分 **割**」類型活動可讓您將目標分割為數個子集。 目標由所有接收結果構成：因此，所有先前的活動都必須完成，才能執行此活動。

此活動不會觸發傳入人口的聯合。 如果多個轉場在一個拆分活動中著陸，建議在 **[!UICONTROL Union]** 其前面插入活動。

有關使用的拆分活動的示例，請參閱使 [用拆分活動建立子集](../../workflow/using/targeting-data.md#creating-subsets-using-the-split-activity)。

本節說明如何使用「分割」活動，使用篩選條件將目標分段為不同的人口族群的范 [例](../../workflow/using/cross-channel-delivery-workflow.md)。

本節提供範例，說明如何在「分割」活動中使用例項變 [數](../../workflow/using/javascript-scripts-and-templates.md)。

若要設定此活動，請在標籤中定義子集內容和標 **[!UICONTROL Subsets]** 簽，然後在標籤中選擇目標 **[!UICONTROL General]** 維度。

## 建立子集 {#creating-subsets}

要建立子集：

1. 按一下相符欄位中的標籤，並選取要套用的篩選。
1. 若要篩選傳入人口，請選取選 **[!UICONTROL Add a filtering condition]** 項，然後按一下 **[!UICONTROL Edit...]** 連結。

   選取要套用至資料的篩選類型，以將其納入此集合中。

   此流程與 **Query**-type活動的流程相同。

   >[!CAUTION]
   >
   >您最多可以篩選兩個外部資料庫(FDA)中的資料。

1. 您可以指定要從目標中提取的最大記錄數以建立子集。 若要這麼做，請勾選選 **[!UICONTROL Limit the selected records]** 項，然後按一下 **[!UICONTROL Edit...]** 連結。

   嚮導可讓您選擇此子集的記錄選擇模式。 這些步驟可在限 [制子集記錄數中找到](#limiting-the-number-of-subset-records)。

   ![](assets/s_user_segmentation_partage4.png)

1. 如果需要，可以使 **用按鈕添加其** 他子 **[!UICONTROL Add]** 集。

   ![](assets/s_user_segmentation_partage_add.png)

   >[!CAUTION]
   >
   >如果未選 **[!UICONTROL Enable overlapping of output populations]** 中該選項，則按頁籤的順序建立子集。 使用此窗口右上方部分的箭頭來移動它們。 例如，如果第一個子集恢復了初始種群的70%，則下一個子集將僅將其選擇標準應用於其餘的30%等。

   對於每個已建立的子集，將向拆分活動添加出站轉移。

   ![](assets/s_user_segmentation_partage_add2.png)

   您可以選擇產生單一對外轉移（並使用區段代碼識別集）:若要這麼做，請選取 **[!UICONTROL Generate subsets in the same table]** 標籤中的選 **[!UICONTROL General]** 項。

   如果完成，每個子集的區段代碼會自動儲存在額外的欄中。 此欄可在傳送層級的個人化欄位中存取。

## 限制子集記錄數 {#limiting-the-number-of-subset-records}

如果您不想使用子集中包含的全部人口，可以限制其將包含的記錄數。

1. 在子集編輯窗口中，選中該選 **[!UICONTROL Limit the selected records]** 項並按一下該 **[!UICONTROL Edit...]** 連結。
1. 選擇您選擇的限制類型：

   * **[!UICONTROL Activate random sampling]**:此選項會隨機取樣記錄。 所套用的隨機取樣類型取決於資料庫引擎。
   * **[!UICONTROL Keep only the first records after sorting]**:此選項可讓您根據一或多個排序順序定義限制。 如果選擇字 **[!UICONTROL Age]** 段作為排序標準，100作為限制，則僅保留最小的100個收件者。
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**:此選項會結合前兩個選項。 它可讓您根據一或多個排序順序定義限制，然後在某些記錄與定義的標準具有相同值時，對第一個記錄套用隨機選擇。

      例如，如果您選取欄位作為排序標準，然後定義100個限制，但資料庫中2000個最年輕的收件者都是18個，則100個收件者會從2000個中隨機選取。 **[!UICONTROL Age]**
   ![](assets/s_user_segmentation_partage_wz1.png)

1. 如果要定義排序標準，則可通過附加步驟定義列和排序順序。

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 然後選擇資料限制方法。

   ![](assets/s_user_segmentation_partage_wz2.png)

   有幾種方法可以做到：

   * **[!UICONTROL Size (in %)]**:百分比的記錄。 例如，以下配置會提取總人口的10%。

      該百分比適用於初始人口，而非活動的結果。

   * **[!UICONTROL Size (as a % of the segment)]**:僅與子集相關而不是與初始種群相關的記錄的百分比。
   * **[!UICONTROL Maximum size]**:最大記錄數。
   * **[!UICONTROL By data grouping]**:您可以根據入站人口的指定欄位中的值，設定記錄數的限制。 有關此主題的詳細資訊，請參 [閱按資料分組限制子集記錄數](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data grouping (in %)]**:您可以根據傳入人口的指定欄位中的值，使用百分比來設定記錄數量限制。 有關此主題的詳細資訊，請參 [閱按資料分組限制子集記錄數](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data distribution]**:如果您的群組欄位有太多值，或您不想再為每個新的分割活動再次輸入值，Adobe Campaign可讓您設定限制(選用的「分 **[!UICONTROL By data distribution]** 布式行銷」模組)。 有關詳細資訊，請參 [閱限制每個資料分發的子集記錄數](#limiting-the-number-of-subset-records-per-data-distribution)。

1. 按一下 **[!UICONTROL Finish]** 以批准記錄選擇標準。 然後，定義的配置將顯示在編輯器的中間窗口中。

## 通過資料分組限制子集記錄數 {#limiting-the-number-of-subset-records-by-data-grouping}

您可以依據資料分組限制記錄數。 此限制可使用固定值或百分比來執行。

例如，如果您選取欄 **[!UICONTROL Language]** 位作為群組欄位，則可以為每個語言定義記錄清單。

1. 選取資料限制值後，選取或 **[!UICONTROL By data grouping]** 按一 **[!UICONTROL By data grouping (as a %)]** 下並按 **[!UICONTROL Next]**&#x200B;下。

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 然後選取群組欄位(例 **[!UICONTROL Language]** 項欄位)，然後按一下 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 最後，指定資料分組臨界值（使用固定值或百分比，視先前選取的分組方法而定）。 要為每個值設定相同的閾值，例如，如果要將每種語言的記錄數設定為10，請選擇選 **[!UICONTROL All data groupings are the same size]** 項。 若要為每個值設定不同的限制，請選取 **[!UICONTROL Limitations by grouping value]** 選項。 這可讓您針對英文、法文等選擇不同的限制。

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 按一 **[!UICONTROL Finish]** 下以核准限制並返回編輯分割活動。

## 限制每個資料分發的子集記錄數 {#limiting-the-number-of-subset-records-per-data-distribution}

如果您的群組欄位包含的值過多，或您不想重設每個新分割活動的值，Adobe Campaign可讓您針對資料分發建立限制。 選擇資料限制值時(有關此主題的詳細資訊，請參閱「 [Creating subsets](#creating-subsets) 」(建立子集 **[!UICONTROL By data distribution]** )，請選擇選項並從下拉菜單中選擇模板。 建立資料分發範本的說明如下。

有關具有分發模 **[!UICONTROL Local approval]** 板的活動示例，請參 [閱使用本地批准活動](../../workflow/using/using-the-local-approval-activity.md)。

![](assets/s_user_segmentation_partage_wz6.png)

>[!CAUTION]
>
>若要使用此函式，您必須購買Distributed Marketing模組，此為促銷活動選項。 請檢查您的授權合約。

資料分發範本可讓您使用分組值清單來限制記錄數。 若要建立資料分發範本，請套用下列步驟：

1. 若要建立資料分發範本，請移至節 **[!UICONTROL Resources > Campaign management > Data distribution]** 點並按一下 **[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. 此標 **[!UICONTROL General]** 簽可讓您輸入分發的標籤和執行內容（定位維度、分發欄位）。

   ![](assets/local_validation_data_distribution_2.png)

   需要輸入下列欄位：

   * **[!UICONTROL Label]**:標籤。
   * **[!UICONTROL Targeting dimension]**:例如，輸入要套用資料分發的目標 **[!UICONTROL Recipient]** 維度。 此架構必須始終與定位工作流程中使用的資料相容。
   * **[!UICONTROL Distribution field]**:透過定位維度選取欄位。 例如，如果您選取欄 **[!UICONTROL Email domain]** 位，收件者清單會依網域劃分。
   * **[!UICONTROL Distribution type]**:在頁籤中選擇目標限制值的劃分方 **[!UICONTROL Distribution]** 式：或 **[!UICONTROL Percentage]** 者 **[!UICONTROL Set]**。
   * **[!UICONTROL Assignment type]**:選擇資料分發分配類型。 您可以按組或運算子選擇分配，或按本地實體選擇分配。 「分佈式行銷」中會使用由本機實 **體指派的作業**。 For more information, refer to this [section](../../campaign/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**:如果您在定位 **[!UICONTROL Local approval]** 工作流程中使用活動(請參 [閱本機核准](../../workflow/using/local-approval.md))，請輸入將儲存核准結果的方案。 每個目標方案必須指定一個儲存方案。 如果使用定位 **[!UICONTROL Recipients]** 結構，請輸入預設的存 **[!UICONTROL Local approval of recipients]** 儲結構。

      如果資料群組不經本機核准而造成簡單限制，則不需要輸入欄 **[!UICONTROL Approvals storage]** 位。

1. 如果您使用活 **[!UICONTROL Local approval]** 動(請參 [閱本地批准](../../workflow/using/local-approval.md))，請輸 **[!UICONTROL Advanced settings]** 入分配模板：

   ![](assets/local_validation_data_distribution_3.png)

   需要輸入下列欄位：

   * **[!UICONTROL Approve targeted messages]**:如果您希望從收件者清單中預先選取所有收件者，請勾選此選項。 如果取消選取此選項，則不會預先選取任何收件者。

      >[!NOTE]
      >
      >此選項預設為勾選。

      ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**:可讓您定義運算式，以在傳回通知中顯示傳送標籤。 預設運算式提供傳送（計算字串）之標準標籤的資訊。 您可以修改此表達式。

      ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**:此欄位可讓您定義群組，以在核准和傳回通知中顯示收件者。

      ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**:可讓您將Web應用程式連結至收件者清單。 在核准和傳回通知中，每個收件者都可點按，並連結至選取的網頁應用程式。 欄 **[!UICONTROL Parameters]** 位(例如 **[!UICONTROL recipientId]**)可讓您設定要用於URL和Web應用程式的其他參數。

      ![](assets/local_validation_notification_5.png)

1. 此標 **[!UICONTROL Breakdown]** 簽可讓您定義分佈值清單。

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**:輸入分配值。
   * **[!UICONTROL Percentage / Set]**:輸入連結至每個值的記錄限制（固定或百分比）。

      此列由頁籤中 **[!UICONTROL Distribution type]** 的欄位定 **[!UICONTROL General]** 義。

   * **[!UICONTROL Label]**:輸入連結至每個值的標籤。
   * **[!UICONTROL Group or operator]**:如果您使用活 **[!UICONTROL Local approval]** 動(請參 [閱本機核准](../../workflow/using/local-approval.md))，請選取指派給每個分配值的運算元或運算元群組。

      如果資料群組不經本機核准而造成簡單限制，則不需要輸入欄 **[!UICONTROL Group or operator]** 位。

      >[!CAUTION]
      >
      >請確定已為運算子指派適當的權限。

   * **[!UICONTROL Local entity]**:選擇分配給每個分佈值的本地實體。 本機實體用於分 **布式行銷**。 For more information, refer to this [section](../../campaign/using/about-distributed-marketing.md).

## 篩選參數 {#filtering-parameters}

按一下該 **[!UICONTROL General]** 頁籤以輸入活動標籤。 選取此分割的目標和篩選維度。 如有必要，您可以變更指定子集的這些維度。

![](assets/s_user_segmentation_partage_general.png)

如果您 **[!UICONTROL Generate complement]** 想利用剩餘人口，請勾選選項。 補數是傳入目標減去子集的並。 然後，活動中將添加一個額外的出站轉移，如下所示：

![](assets/s_user_segmentation_partage_compl.png)

要使此選項正常運作，入站資料必須具有主鍵。

例如，如果資料是透過活動直接從外部資料庫（例如不支援索引概念的Netezza）讀取 **[!UICONTROL Data loading (RDBMS)]** ，則活動產生的補 **[!UICONTROL Split]** 碼將不正確。

若要避免此情況，您可以在活動前 **[!UICONTROL Enrichment]** 拖放活 **[!UICONTROL Split]** 動。 在活 **[!UICONTROL Enrichment]** 動中，檢 **[!UICONTROL Keep all additional data from the main set]** 查並在其他資料中指定要用於配置活動篩選器的列 **[!UICONTROL Split]** 。 然後，活動傳入轉場中的資 **[!UICONTROL Split]** 料會儲存在Adobe Campaign伺服器上的臨時表格中，並可正確產生補碼。

此選 **[!UICONTROL Enable overlapping of output populations]** 項可讓您管理屬於數個子集的人口族群：

* 如果未勾選此方塊，分割活動會確保收件者無法出現在數個輸出轉場中，即使符合數個子集的標準亦然。 它們將位於第一個具有匹配條件的頁籤的目標中。
* 勾選方塊後，如果收件者符合其篩選條件，就可以在數個子集中找到。 Adobe Campaign建議使用獨家標準。

## 輸入參數 {#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這組三個值識別排除所產生的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補體相關的過渡具有相同的參數。
