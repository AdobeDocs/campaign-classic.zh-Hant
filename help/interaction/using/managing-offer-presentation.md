---
solution: Campaign Classic
product: campaign
title: 管理優惠方案簡報
description: 管理優惠方案簡報
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---


# 管理優惠方案簡報{#managing-offer-presentation}

## 演示規則概述{#presentation-rules-overview}

互動功能可讓您使用簡報規則來控制優惠提案的流程。 這些規則是「互動」專屬的類型學規則。 它們可讓您根據已向收件者提出之主張的歷史記錄，排除選件。 在環境中引用它們

## 建立和參考選件簡報規則{#creating-and-referencing-an-offer-presentation-rule}

1. 前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**&#x200B;節點。
1. 建立排版規則並選擇&#x200B;**[!UICONTROL Offer presentation]**&#x200B;類型。

   ![](assets/offer_typology_001.png)

1. 指定規則應套用的渠道。

   ![](assets/offer_typology_002.png)

1. 設定規則的應用程式條件。 有關詳細資訊，請參閱[演示規則設定](#presentation-rule-settings)。
1. 前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]**&#x200B;節點，並建立將所有&#x200B;**[!UICONTROL Offer presentation]**&#x200B;類型規則分組的類型學。

   ![](assets/offer_typology_003.png)

1. 在建立類型後，將游標置於類型學規則上，並將它們分組到您剛建立的類型學中。

   ![](assets/offer_typology_004.png)

1. 在您的選件環境中，使用下拉式清單來參考類型學。

   ![](assets/offer_typology_005.png)

## 演示規則設定{#presentation-rule-settings}

### 應用程式條件{#application-criteria-}

**[!UICONTROL General]**&#x200B;標籤中可用的應用程式條件可讓您指定要套用簡報規則的選件。 若要這麼做，您必須建立查詢並選擇相關選件，如下所述。

1. 在您的排版規則中，按一下&#x200B;**[!UICONTROL Edit the rule application conditions...]**&#x200B;連結以建立查詢。

   ![](assets/offer_typology_006.png)

1. 在查詢視窗中，您可以對要套用排版規則的選件套用篩選。

   例如，您可以選取選件類別。

   ![](assets/offer_typology_008.png)

### 選件維度{#offer-dimensions}

在&#x200B;**[!UICONTROL Offer presentation]**&#x200B;標籤中，您必須為表示規則指定與環境中配置的維相同的維。

**[!UICONTROL Targeting dimension]**&#x200B;與收件者表格一致(預設為：nms：收件者)，他們將接收選件建議。 **[!UICONTROL Storage dimension]**&#x200B;與包含與目標維連結的命題歷史記錄的表一致（預設情況下：nms:compositionRcp）。

![](assets/offer_typology_009.png)

>[!NOTE]
>
>您也可以使用非標準表格。 如果您想使用特定的定位維度，則需要使用定位映射來建立表格和專用環境。 有關詳細資訊，請參閱[建立選件環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

### 期間{#period}

這是滑動時段，從選件簡報日期開始。 它為選件的有效性設定了時限。 該規則不適用於在此期間之後提出的建議。

該期間在提案日期前開始&#x200B;**n**&#x200B;天，在提案日期後結束&#x200B;**n**&#x200B;天，其中&#x200B;**n**&#x200B;對應於在&#x200B;**[!UICONTROL Period considered]**&#x200B;欄位中輸入的數字：

* 對於傳入空間，提案日期是選件簡報日期。
* 對於出站空間，建議日期是交貨聯繫日期（例如在定位工作流中輸入的交貨日期）。

使用箭頭來變更天數或直接輸入期間（例如「2d 6h」）。

![](assets/offer_typology_010.png)

### 命題數{#number-of-propositions}

可以設定在排除相關選件之前可以提出的最大數目的建議。

使用箭頭來變更選件的數目。

![](assets/offer_typology_011.png)

## 定義主張和收件人{#defining-propositions-and-recipients}

**[!UICONTROL Propositions to count]**&#x200B;區段可讓您指定收件者和主張，如果這些收件者和主張在主張歷史記錄中出現特定次數，則會排除在&#x200B;**[!UICONTROL General]**&#x200B;標籤中定義的選件。

### 篩選命題{#filtering-propositions}

您可以選擇篩選條件，以根據渠道、相關選件或先前指派之主張的狀態排除主張。

![](assets/offer_typology_014.png)

這些准則代表表現規則最常用的應用程式。 若要使用其他條件，可以使用&#x200B;**[!UICONTROL Limit propositions...]**&#x200B;連結建立查詢。 有關詳細資訊，請參閱[建立關於命題的查詢](#creating-a-query-on-propositions)部分。

* **在頻道上篩選**

   **[!UICONTROL On the same channel only]** :可讓您排除標籤中指定之渠道上的選件 **[!UICONTROL General]** 主張。

   例如，在&#x200B;**[!UICONTROL General]**&#x200B;標籤中為規則指定的渠道是電子郵件。 如果規則所套用的選件目前僅在Web頻道上提供，互動引擎可以在電子郵件傳送中呈現選件。 不過，當選件以電子郵件呈現後，互動引擎會選擇不同的渠道來呈現選件。

   >[!NOTE]
   >
   >我們說的是頻道，而不是空間。 如果規則必須排除網頁頻道上的選件，則網站上不會顯示該選件（例如橫幅和頁面內文），如果該選件之前已經顯示過。
   >
   >對於涉及選件簡報的工作流程，只有在&#x200B;**[!UICONTROL All channels]**&#x200B;上設定規則時，才會正確考量規則。

* **篩選選件**

   此篩選器可讓您將選件命題限制為特定選件集。

   **[!UICONTROL All offers]** :預設值。選件不會套用任何篩選。

   **[!UICONTROL Offer being presented]** :如果已顯示選 **[!UICONTROL General]** 項卡中指定的選件，則會排除它。

   **[!UICONTROL Offers from the same category]** :如果已顯示相同類別的選件，則會排除選件。

   **[!UICONTROL The offers which the rule applies to]** :在標籤中定義數個選 **[!UICONTROL General]** 件時，會考慮此組選件中的每個選件提案，並在達到提案臨界值時排除所有選件。

   例如，選件2、3和5在&#x200B;**[!UICONTROL General]**&#x200B;標籤中定義。 命題的最大數設定為2。 如果選件2和5各呈現一次，則計算的主張數為2。 因此，優惠3永遠不會出現。

* **篩選提案狀態**

   此篩選器可讓您為提案歷史記錄中要考慮的選件提案選擇最頻繁的狀態。

   **[!UICONTROL Regardless of the proposition status]** :預設值。提案狀態不會套用任何篩選。

   **[!UICONTROL Accepted or rejected propositions]** :可讓您排除先前已接受或拒絕的提案。

   **[!UICONTROL Accepted propositions]** :可讓您排除先前已接受的呈現選件。

   **[!UICONTROL Rejected propositions]** :可讓您排除先前呈現且已遭拒絕的選件。

### 定義收件者{#defining-recipients}

若要指定收件者，請按一下&#x200B;**[!UICONTROL Edit the query from the targeting dimension...]**&#x200B;連結，然後選取規則所關注的收件者。

![](assets/offer_typology_012.png)

### 建立關於命題{#creating-a-query-on-propositions}的查詢

要指定要通過查詢計算的主張，請按一下&#x200B;**[!UICONTROL Limit propositions...]**&#x200B;連結並指定要考慮的標準。

在以下示例中，在兩次演示後要計算的命題是&#x200B;**特殊選件**&#x200B;類別中&#x200B;**呼叫中心**&#x200B;空間的主題，其權重低於&#x200B;**20**。

![](assets/offer_typology_013.png)

