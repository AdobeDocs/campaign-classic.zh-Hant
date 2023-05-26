---
product: campaign
title: Adobe Campaign Classic互動最佳實務
description: 本節提供在Adobe Campaign Classic中管理互動模組的最佳實務方法
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 98413cde-50c9-416c-8316-85837f724c27
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1193'
ht-degree: 0%

---

# 互動最佳實務{#interaction-best-practices}



## 一般性建議 {#general-recommendations}

本節提供在Adobe Campaign Classic中管理互動模組的最佳實務方法，包括適用性規則、預先定義的篩選器、工作流程活動和資料庫選項。

Adobe Campaign中的互動需要謹慎管理，才能有效率地運作。 您必須找到連絡人數目與優惠方案類別與優惠方案數目之間的平衡。 若未妥善處理這些因素，您的Adobe Campaign執行個體可能會遇到問題。

### 實作 {#implementation}

以下列出實作和設定互動時應牢記的重要元素。

* 對於批次引擎（通常用於電子郵件等對外通訊），吞吐量是主要問題，因為可以同時處理多個聯絡人。 典型的瓶頸是資料庫效能。
* 單一引擎的主要限制（通常用於網站橫幅之類的傳入通訊）是延遲，因為有人會期待答案。 典型的瓶頸是CPU效能。
* 優惠方案目錄設計對Adobe Campaign Classic的效能有巨大影響。
* 當有許多優惠方案時，請將其分割為多個優惠方案目錄。

### 適用性規則 {#eligibility-rules}

以下列出適用性規則的一些最佳實務。

* 簡化規則。 規則的複雜性會隨著查詢的延長而影響效能。 複雜規則是指具有五個以上條件的任何規則。
* 為了提高效能，可以在多個選件之間共用的不同預先定義篩選器中劃分規則。
* 將限制最嚴格的選件類別規則放在樹狀結構中最高的位置。 這樣一來，他們會先篩選掉最多聯絡人，減少目標數量，並防止他們受到其他規則的處理。
* 將時間或處理成本最高的規則放在樹狀結構底部。 如此一來，這些規則將只在剩餘的目標對象上執行。
* 從特定類別開始，以避免掃描整個樹狀結構。
* 為了節省處理時間，請預先計算彙總，而非使用聯結建立複雜的規則。 若要這麼做，請嘗試將客戶資料儲存在參考表格中，可在適用性規則中查詢該表格。
* 使用最小加權數來限制查詢數。
* 建議每個選件空間中的選件數量有限。 這可確保在任何指定空間中更快速地擷取選件。
* 使用索引，尤其是在常用的查閱資料行上。

### 主張表格 {#proposition-table}

以下列出一些關於主張表格的最佳實務。

* 使用最少數量的規則，以儘快完成處理。
* 限制主張表格中的記錄數量：僅保留追蹤其狀態更新及規則所需內容所需的記錄，然後將它們封存至其他系統。
* 對主張表格執行密集的資料庫維護，例如重建索引或重新建立表格。
* 限制每個目標要求的主張數量。 請勿設定超過您實際要使用的專案。
* 在規則條件中儘可能避免聯結。

## 管理優惠方案的秘訣與技巧 {#tips-managing-offers}

本節包含有關管理優惠方案及使用Adobe Campaign Classic中的互動模組的更多詳細建議。

### 在電子郵件傳遞中使用多個優惠方案空間 {#multiple-offer-spaces}

在傳遞中包含優惠方案時，通常會透過擴充活動（或其他類似活動）在行銷活動工作流程的上游選取優惠方案。

在擴充活動中選取優惠方案時，您可以選擇要使用哪個優惠方案空間。 但是，無論選取的優惠方案空間為何，傳遞自訂功能表都取決於傳遞中設定的優惠方案空間。

在以下範例中，在傳送中選取的優惠方案空間為 **[!UICONTROL Email (Environment - Recipient)]**：

![](assets/Interaction-best-practices-offer-space-selected.png)

如果您在傳送中選取的優惠方案空間未設定HTML演算功能，您將無法在傳送功能表中看到該空間，也無法加以選取。 同樣地，這與擴充活動中選取的優惠方案空間無關。

在以下範例中，下拉式清單中提供HTML轉譯函式，因為傳送中選取的選件空間具有轉譯函式：

![](assets/Interaction-best-practices-HTML-rendering.png)

此函式插入程式碼，例如： `<%@ include proposition="targetData.proposition" view="rendering/html" %>`.

當您選取主張時， **[!UICONTROL view]** 屬性如下：
* &quot;rendering/html&quot;： html rendering. 它會使用HTML演算函式。
* &quot;offer/view/html&quot;： html內容。 它不使用HTML演算函式。 它只包含HTML欄位。

當您在單一電子郵件傳遞中包含多個選件空間時，如果其中有些選件具有轉譯函式，有些則沒有，您必須記住哪些選件使用哪些選件空間，以及哪些選件空間具有轉譯函式。

因此，為避免任何問題，建議所有選件空間都定義有HTML呈現函式，即使您的選件空間只需要HTML內容。

### 在主張記錄表中設定排名 {#rank-proposition-log-table}

當產生或接受建議時，優惠方案空間能夠儲存主張表格中的資料：

![](assets/Interaction-best-practices-offer-space-storage.png)

但是，這僅適用於傳入互動。

使用傳出互動時，以及使用沒有互動模組的傳出選件時，也可以在主張表格中儲存其他資料。

工作流程暫存表格中名稱與主張表格中欄位名稱相符的任何欄位，都會複製到主張表格的相同欄位中。

例如，在「擴充」中手動選取優惠方案（無互動）時，標準欄位的定義如下：

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

可以新增其他欄位，例如@rank欄位：

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

由於主張表格中有一個名為@rank的欄位，因此將會複製工作流程暫存表格中的值。

如需在主張表格中儲存其他欄位的詳細資訊，請參閱 [透過工作流程整合優惠方案](../../interaction/using/integrating-an-offer-via-a-workflow.md#storing-offer-rankings-and-weights).

若為具有互動的傳出優惠方案，當您選取數個優惠方案，並想要記錄它們在電子郵件中的顯示順序時，此功能會很實用。

您也可以直接在主張表格中儲存其他中繼資料（例如目前的支出層級），以保留產生優惠方案時支出的歷史記錄。

使用「出埠互動」時，可以新增@rank欄位（如上述範例所示），但其值會根據「互動」傳回的訂單自動設定。 例如，如果您使用「互動」來選取三個優惠方案，@rank欄位會傳回值1、2和3。

使用互動和手動選取優惠方案時，使用者可以將兩種方法結合使用。 例如，使用者可以手動將手動選取之優惠的@rank欄位設為1，並針對Interaction傳回的優惠使用如&quot;1 + @rank&quot;的運算式。 假設「互動」選取了三個優惠方案，這兩種方法傳回的優惠方案排名將為1-4：

![](assets/Interaction-best-practices-manual-offer-combined.png)

### 擴充nms：offer綱要 {#extending-nms-offer-schema}

擴充nms：offer結構描述時，請務必遵循已設定的現成結構：
* 定義下內容儲存的任何新欄位 `<element name="view">`.
* 每個新欄位需要定義兩次。 一次作為一般XML欄位，另一次作為CDATA XML欄位，並在名稱后附加「_jst」。 例如：

   ```
   <element label="Price" name="price" type="long" xml="true"/>
   <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
   ```

* 包含要追蹤之URL的任何欄位都必須放在 `<element name="trackedUrls">` ，位於 `<element name="view" >`.
