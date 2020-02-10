---
title: 管理選件簡報
seo-title: 管理選件簡報
description: 管理選件簡報
seo-description: null
page-status-flag: never-activated
uuid: cf4614b9-a322-4170-aa6d-4f138f8ca2d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: f6e44634-3a13-480e-ab44-f3c744054a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 管理選件簡報{#managing-offer-presentation}

## 簡報規則概觀 {#presentation-rules-overview}

互動功能可讓您使用簡報規則來控制優惠提案的流程。 這些規則是「互動」專屬的類型學規則。 它們可讓您根據已向收件者提出之主張的歷史記錄，排除選件。 在環境中引用它們

## 建立和參考選件簡報規則 {#creating-and-referencing-an-offer-presentation-rule}

1. 前往 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** >節 **[!UICONTROL Typology rules]** 點。
1. 建立排版規則並選擇 **[!UICONTROL Offer presentation]** 類型。

   ![](assets/offer_typology_001.png)

1. 指定規則應套用的渠道。

   ![](assets/offer_typology_002.png)

1. 設定規則的應用程式條件。 如需詳細資訊，請參閱「簡報 [規則設定」](#presentation-rule-settings)。
1. 前往 **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** >節點，並建立將所有類型規則 **[!UICONTROL Typologies]****[!UICONTROL Offer presentation]** 分組的類型。

   ![](assets/offer_typology_003.png)

1. 在建立類型後，將游標置於類型學規則上，並將它們分組到您剛建立的類型學中。

   ![](assets/offer_typology_004.png)

1. 在您的選件環境中，使用下拉式清單來參考類型學。

   ![](assets/offer_typology_005.png)

## 簡報規則設定 {#presentation-rule-settings}

### 應用程式條件 {#application-criteria-}

標籤中可用的應用程 **[!UICONTROL General]** 式條件可讓您指定要套用簡報規則的選件。 若要這麼做，您必須建立查詢並選擇相關選件，如下所述。

1. 在您的排版規則中，按一下 **[!UICONTROL Edit the rule application conditions...]** 連結以建立查詢。

   ![](assets/offer_typology_006.png)

1. 在查詢視窗中，您可以對要套用排版規則的選件套用篩選。

   例如，您可以選取選件類別。

   ![](assets/offer_typology_008.png)

### 選件維度 {#offer-dimensions}

在標籤 **[!UICONTROL Offer presentation]** 中，您必須指定與環境中配置的相同表現規則維度。

此 **[!UICONTROL Targeting dimension]** 值與收件者表格一致(預設為：nms：收件者)，他們將接收選件建議。 該 **[!UICONTROL Storage dimension]** 表與包含連結到目標維的命題歷史記錄的表一致（預設情況下：nms:compositionRcp）。

![](assets/offer_typology_009.png)

>[!NOTE]
>
>您也可以使用非標準表格。 如果您想使用特定的定位維度，則需要使用定位映射來建立表格和專用環境。 如需詳細資訊，請參閱「 [建立選件環境」](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

### 期間 {#period}

這是滑動時段，從選件簡報日期開始。 它為選件的有效性設定了時限。 該規則不適用於在此期間之後提出的建議。

期間在提 **案日期** n天前開始，在 **n天后結束，其中** n **與在欄位中輸入的****[!UICONTROL Period considered]** 數字：

* 對於傳入空間，提案日期是選件簡報日期。
* 對於出站空間，建議日期是交貨聯繫日期（例如在定位工作流中輸入的交貨日期）。

使用箭頭來變更天數或直接輸入期間（例如「2d 6h」）。

![](assets/offer_typology_010.png)

### 命題數 {#number-of-propositions}

可以設定在排除相關選件之前可以提出的最大數目的建議。

使用箭頭來變更選件的數目。

![](assets/offer_typology_011.png)

## 定義主張和收件人 {#defining-propositions-and-recipients}

本節 **[!UICONTROL Propositions to count]** 可讓您指定收件者和主張，如果選件在主張歷史記錄中出現特定次數，則會排除 **[!UICONTROL General]** 標籤中定義的選件。

### 篩選命題 {#filtering-propositions}

您可以選擇篩選條件，以根據渠道、相關選件或先前指派之主張的狀態排除主張。

![](assets/offer_typology_014.png)

這些准則代表表現規則最常用的應用程式。 若要使用其他條件，您可以使用連結建立 **[!UICONTROL Limit propositions...]** 查詢。 有關此的詳細資訊，請參 [閱「建立命題查詢](#creating-a-query-on-propositions) 」部分。

* **在頻道上篩選**

   **[!UICONTROL On the same channel only]** :可讓您排除標籤中指定之渠道上的選件 **[!UICONTROL General]** 主張。

   例如，標籤中為規則指定的渠道 **[!UICONTROL General]** 是電子郵件。 如果規則所套用的選件目前僅在Web頻道上提供，互動引擎可以在電子郵件傳送中呈現選件。 不過，當選件以電子郵件呈現後，互動引擎會選擇不同的渠道來呈現選件。

   >[!NOTE]
   >
   >我們說的是頻道，而不是空間。 如果規則必須排除網頁頻道上的選件，則網站上不會顯示該選件（例如橫幅和頁面內文），如果該選件之前已經顯示過。
   >
   >對於涉及選件簡報的工作流程，只有在設定規則時，才會正確考量規則 **[!UICONTROL All channels]**。

* **篩選選件**

   此篩選器可讓您將選件命題限制為特定選件集。

   **[!UICONTROL All offers]** :預設值。 選件不會套用任何篩選。

   **[!UICONTROL Offer being presented]** :標籤中指定的選 **[!UICONTROL General]** 件如果已顯示，則會排除該選件。

   **[!UICONTROL Offers from the same category]** :如果已顯示相同類別的選件，則會排除選件。

   **[!UICONTROL The offers which the rule applies to]** :在標籤中定義數個選 **[!UICONTROL General]** 件時，會考慮此組選件中的每個選件提案，並在達到提案臨界值時排除所有選件。

   例如，選件2、3和5在標籤中定 **[!UICONTROL General]** 義。 命題的最大數設定為2。 如果選件2和5各呈現一次，則計算的主張數為2。 因此，優惠3永遠不會出現。

* **篩選提案狀態**

   此篩選器可讓您為提案歷史記錄中要考慮的選件提案選擇最頻繁的狀態。

   **[!UICONTROL Regardless of the proposition status]** :預設值。 提案狀態不會套用任何篩選。

   **[!UICONTROL Accepted or rejected propositions]** :可讓您排除先前已接受或拒絕的提案。

   **[!UICONTROL Accepted propositions]** :可讓您排除先前已接受的呈現選件。

   **[!UICONTROL Rejected propositions]** :可讓您排除先前呈現且已遭拒絕的選件。

### 定義收件者 {#defining-recipients}

若要指定收件者，請按一下 **[!UICONTROL Edit the query from the targeting dimension...]** 連結並選取規則所關注的收件者。

![](assets/offer_typology_012.png)

### 建立關於命題的查詢 {#creating-a-query-on-propositions}

若要指定要透過查詢計算的命題，請按一 **[!UICONTROL Limit propositions...]** 下連結並指定要考慮的准則。

在下例中，在兩次演示後要計算的主張是「特殊選件」類別中的主張，適用於 **「客服中心** 」空間，其權重低於 **20******。

![](assets/offer_typology_013.png)

