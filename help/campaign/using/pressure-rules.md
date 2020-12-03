---
solution: Campaign Classic
product: campaign
title: 壓力規則
description: 壓力規則
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '3253'
ht-degree: 4%

---


# 壓力規則{#pressure-rules}

## 關於行銷疲勞{#about-marketing-fatigue}

實施銷售壓力管理可讓您避免過多地招攬資料庫中的人口，也稱為行銷疲勞。 若要這麼做，您可以定義每個收件者的訊息數量上限。 此外，它還可讓您在促銷活動之間實作仲裁規則，以便傳送最佳訊息給目標對象。

**壓** 制規則，以管理行銷疲勞，例如，將要傳送給一群用戶的信件數限制為2，選擇最符合一群用戶利益的通訊方式，避免傳送簡訊給不滿意的客戶等。

促銷活動會根據定義的臨界值和訊息權重來選取。

* 臨界值是指定期間內授權給特定接收者的最高遞送數。 可以是設定或變數。 在排版規則設定中設定或計算。 請參閱[消息數上限](#maximum-number-of-messages)。
* 交付權重可讓您在壓力管理框架內識別最優先的交付。 具有最大權重的消息具有優先順序。 請參閱[消息權重](#message-weight)。

仲裁包括確保重量大於進行中促銷活動的已排程促銷活動不會導致過多描述檔請求：如果是這樣，則會從傳送中排除描述檔。

仲裁標準（消息權重和／或閾值）可能因兩種資訊類型而異：

* 收件者偏好設定，即宣告資訊：電子報訂閱，收件者狀態（客戶或潛在客戶）,
* 收件者行為：購買、瀏覽的連結等。

用於定義合格消息的仲裁規則在分析階段期間應用。 對於每位收件者和相關期間，如果下列公式成立，則會傳送訊息：**（已發送的消息數）+（具有較大權重的消息數）&lt;閾值**。

否則，收件者將是&#x200B;**[!UICONTROL Excluded by arbitration]**。 有關詳情，請參閱[仲裁後排除](#exclusion-after-arbitration)。

## 建立壓力規則{#creating-a-pressure-rule}

若要使用Adobe Campaign在促銷活動之間設定仲裁，請先建立促銷活動類型並定義連結的類型規則（**壓力**&#x200B;規則）。

若要建立與設定 **[!UICONTROL Pressure]** 類型規則，請套用下列步驟：

1. 在促銷活動類型規則清單中，按一下清單上方的&#x200B;**[!UICONTROL New]**&#x200B;圖示。

   ![](assets/campaign_opt_create_a_rule_01.png)

1. 在新規則的&#x200B;**[!UICONTROL General]**&#x200B;標籤中，選擇&#x200B;**壓力**&#x200B;類型規則，並輸入其名稱和說明。

   ![](assets/campaign_opt_create_a_rule_02.png)

1. 視需要變更執行順序。 當套用多個排版規則為&#x200B;**[!UICONTROL Typology]**&#x200B;集時，會先套用順序較低的規則。 有關詳細資訊，請參閱[執行順序](../../campaign/using/applying-rules.md#execution-order)。
1. 在&#x200B;**[!UICONTROL Calculation parameters]**&#x200B;區段中，如果您想要儲存定位超過下次每日重新仲裁執行的頻率，請定義頻率。 有關詳細資訊，請參閱[調整計算頻率](../../campaign/using/applying-rules.md#adjusting-calculation-frequency)。
1. 按一下&#x200B;**[!UICONTROL Pressure]**&#x200B;標籤，然後選擇套用排版規則的日曆期間。

   ![](assets/campaign_opt_create_a_rule_03.png)

   該規則將應用於將聯繫日期納入有關期間的交貨。

   >[!NOTE]
   >
   >只有在選取&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**&#x200B;選項時，才會考慮排程的傳送。 有關詳細資訊，請參閱[設定句點](#setting-the-period)。

1. 定義計算最大消息數的方法。

   該閾值表示在相關期間可發送給接收者的消息的最大數量。

   依照預設，臨界值為常數，您必須指出該規則授權的訊息數量上限。

   ![](assets/campaign_opt_create_a_rule_03b.png)

   要定義變數閾值，請在&#x200B;**[!UICONTROL Type of threshold]**&#x200B;欄位中選擇&#x200B;**[!UICONTROL Depends on the recipient]**&#x200B;值，然後使用右側的表徵圖開啟表達式編輯器。

   ![](assets/campaign_opt_create_a_rule_04.png)

   有關詳細資訊，請參閱[最大消息數](#maximum-number-of-messages)。

1. 指定計算傳送重量的方法。

   每個傳送都有權重，即表示其優先順序的值：這可讓促銷活動之間進行仲裁。 權重是使用在類型學規則和／或其屬性中定義的公式計算的。 有關詳細資訊，請參閱[消息權重](#message-weight)。

1. 預設情況下，所有訊息都將考慮到臨界值計算。**[!UICONTROL Restriction]**&#x200B;標籤可讓您篩選與排版規則相關的訊息：

   * 此標籤的上方區段可讓您限制相關收件者。
   * 此標籤的下方區段可讓您篩選要計算的訊息。

      在以下示例中，只考慮保存在&#x200B;**NewContacts**&#x200B;資料夾中的收件人，並考慮從&#x200B;**Newsletter**&#x200B;開始的交貨。
   ![](assets/campaign_opt_create_a_rule_05.png)

1. **[!UICONTROL Typologies]**&#x200B;標籤可讓您檢視套用此規則或將規則連結至一或多個現有類型的促銷活動類型。 有關詳細資訊，請參閱[應用類型](../../campaign/using/about-campaign-typologies.md#applying-typologies)。

## 定義閾值和權重{#defining-thresholds-and-weights}

### 消息數上限{#maximum-number-of-messages}

每個壓力規則定義一個閾值，即在給定時間段內可以發送給一個接收者的消息的最大數量。 一旦達到此臨界值時，在考慮到該期間結束之前，將不再進行傳送。此程式可讓您在訊息超過設定的臨界值時，自動將收件者排除在傳送範圍之外，以避免過度招攬。

臨界值可以是常數，也可以是由含變數的公式計算。 這表示在指定期間，臨界值可能會因收件者而異，甚至因相同的收件者而異。

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>將&#x200B;**0**&#x200B;輸入為閾值可防止在所考慮的期間內向目標人口的所有傳送。

**範例:**

您可以根據收件者所屬的區段，為已授權訊息的數目建立索引。 這表示屬於網頁區段的收件者接收的訊息可能比其他收件者多。 **[!UICONTROL Iif (@origin='Web', 5, 3)]**&#x200B;類型公式可授權傳送5個訊息給收件者，其他區段則授權傳送3個訊息。 配置如下：

![](assets/campaign_opt_pressure_sample.png)

若要定義臨界值，您可以使用連結至定位維度的維度：例如，要包含傳送給訪客表格中儲存之收件者描述檔的訊息（有關訪客表格的詳細資訊，請參閱[本節](../../web/using/use-case--creating-a-refer-a-friend-form.md)），或避免每週傳送多則訊息給同一家庭（可能指數個電子郵件地址），此訊息在連結至收件者的維度中識別。

若要這麼做，請選取&#x200B;**[!UICONTROL Count messages on a linked dimension]**&#x200B;選項，然後選取訪客或連絡人表格。

### 消息重量{#message-weight}

每個傳送都有權重，代表其優先順序。 預設情況下，交貨的重量設定為5。 壓力規則可讓您定義要套用的交貨的重量。

權重可以透過公式設定或計算，以符合收件者。 例如，您可以根據收件者興趣來定義交貨的權重。

>[!CAUTION]
>
>在&#x200B;**[!UICONTROL Properties]**&#x200B;標籤中，在類型學規則中定義的權重可以針對每個傳送分別過載。 按一下&#x200B;**[!UICONTROL Typology]**&#x200B;標籤以選取促銷活動類型，並指定要套用的權重。\
>但是，A類型規則中宣告的權重不會用於計算B類型規則：此權重僅涉及使用A規則的交貨。

**範例:**

在下列範例中，我們想將電子報對音樂的權重與收件者的傾向分數連結。 操作步驟：

1. 建立新欄位以儲存收件者傾向分數。 在本例中，**@Music**&#x200B;欄位將豐富調查和線上投票、收集的追蹤資料等的答案。
1. 建立類型規則，以根據此欄位計算訊息權重。

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. 將此規則應用於具有以下主題的消息：電子報、特別優惠等。 這些遞送的權重，以及其優先順序，將取決於每個收件者的傾向分數。

## 設定句點{#setting-the-period}

壓力規則定義在&#x200B;**n**&#x200B;天滾動週期中。

該句點在規則的&#x200B;**[!UICONTROL Pressure]**&#x200B;標籤中配置。 您可以指定天數，並視需要選取要套用的群組類型（日、周、月、季等）。

分組類型可讓您將&#x200B;**[!UICONTROL Period considered]**&#x200B;欄位延伸至該期間日期的整天、日曆周、日曆月或日曆年。

例如，壓力規則定義每週2則訊息的臨界值（每個日曆月分組），將防止在同一週內傳送超過2則訊息，而在同一日曆月內傳送超過2則訊息。 警告，如果期間與兩個月重疊，計算臨界值將考慮這兩個日曆月的交貨，因此可能會阻止第二個月內的所有新交貨。

>[!NOTE]
>
>依預設，計算臨界值時只會考慮已傳送的傳送。 如果您也想要考慮為相關期間計畫的交貨，請選中&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**&#x200B;選項。 在這種情況下，考慮的期間加倍，以便將未來交貨和以前交貨結合起來。\
>要將考慮的交貨限制在2週期間，您可以執行以下任一操作：
>
>* 在&#x200B;**[!UICONTROL Concerned period]**&#x200B;欄位中輸入&#x200B;**15d**:在運算中，將考慮到在套用規則的交貨日期前兩週前發送的交貨，
>
>  
或
>
>* 在&#x200B;**[!UICONTROL Period considered]**&#x200B;欄位中輸入&#x200B;**7d**，並檢查&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**\
   >選項：在計算時，會考慮到在交貨日期前7天以及在交貨日期後計畫的交貨（最長7天）。
>
>
期間開始日期取決於資料庫的配置方式。

例如，如果您套用15天壓力規則，而未將其分組至日期為12/11的交貨，則11/27至12/12之間的交貨將納入考量。 如果壓力規則考慮臨時日曆中的交貨，則將考慮11/27至12/27之間計畫的所有交貨。 最後，如果您在規則中設定每個日曆月的分組，則在計算臨界值時（從11/1到12/31）會考慮11月和12月的所有交貨。

>[!CAUTION]
>
>**常見案例**
>為確保未考慮當前日曆周的交貨，也不考慮計算閾值的前一週的交貨，請將&#x200B;**[!UICONTROL Period considered]**&#x200B;指定為&#39;0&#39;並選擇「按日曆周分組」作為&#x200B;**[!UICONTROL Period type]**。
> 
>當期間高於0（例如1）時，計算臨界值可能會考慮前一天的傳送。 因此，如果前一天與上一個日曆周對應，而選取的期間類型是「依每個日曆周分組」，則計算臨界值將會計入所有上一週。

**範例:**

我們想要建立壓力規則，限制每2週期間招標3則訊息，並將群組設為日曆月份。

![](assets/campaign_opt_pressure_period_sample_1a.png)

讓我們舉辦6份同樣重量的電子報，排定05/30、06/3、06/8、06/12、06/22和06/30。

![](assets/campaign_opt_pressure_period_sample_0.png)

預定於6月12日和30日交貨的貨物將不寄送：06/12傳送量將超過每2週期間3則訊息的臨界值，而第30次傳送量將超過每個日曆月授權通訊量的臨界值。

![](assets/campaign_opt_pressure_period_sample_1.png)

在分析階段，這些交貨的所有接收者都會被仲裁排除：

![](assets/campaign_opt_pressure_period_sample_2.png)

對於相同規則，如果您將每季的交貨分組，**電子報第5**&#x200B;號的收件者也將被排除，而且不會傳送。

最後，如果未選取任何群組，則只會傳送&#x200B;**電子報第4**&#x200B;號，因為該電子報與前三個電子報排定在相同的2週期間。

>[!NOTE]
>
>當您變更排版規則的定義時，可以建立&#x200B;**Simulation**，以控制其對套用至的遞送的影響，並監控遞送對彼此的影響。 如需詳細資訊，請參閱[促銷活動模擬](../../campaign/using/campaign-simulations.md)。

## 仲裁後排除{#exclusion-after-arbitration}

仲裁會透過&#x200B;**[!UICONTROL Forecasting]**&#x200B;技術工作流程和&#x200B;**[!UICONTROL Campaign jobs]**&#x200B;工作流程每晚重新套用。

**[!UICONTROL Forecasting]**&#x200B;工作流程會預先計算進行中期間（從開始日期到目前日期）的資料，以便在分析期間套用排版規則。 它還會重新計算每晚仲裁的排除計數器。

因此，Adobe Campaign會針對每位收件者檢查要傳送的訊息數量是否超過臨界值，並考慮到相關期間已傳送的訊息數量。 此資訊是&#x200B;**指標**，因為所有計算都會在傳送時更新。

如果此數字超過臨界值，則會套用促銷活動類型學中定義的仲裁規則，並將收件者排除在權重較低的促銷活動之外。

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>如果數個傳送的分數相等，則會傳送排程在最早日期的促銷活動。

## 壓力規則{#use-cases-on-pressure-rules}的使用案例

### 根據{#adapting-the-threshold-based-on-criterion}標準調整閾值

我們想要建立分類規則，以防止每週向客戶傳送超過4封訊息，並防止每週向潛在客戶傳送2封訊息。

若要識別客戶和潛在客戶，請使用&#x200B;**[!UICONTROL Status]**&#x200B;欄位，其中包含0代表潛在客戶，1代表客戶。

若要建立規則，請套用以下步驟：

1. 建立新的&#x200B;**Pressure**&#x200B;類型排版規則。
1. 編輯&#x200B;**[!UICONTROL Pressure]**&#x200B;標籤：在&#x200B;**[!UICONTROL Maximum number of messages]**&#x200B;區段中，我們要建立公式以根據每個收件者計算臨界值。 在&#x200B;**[!UICONTROL Threshold type]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Depends on the recipient]**&#x200B;值，然後按一下&#x200B;**[!UICONTROL Formula]**&#x200B;欄位右側的&#x200B;**[!UICONTROL Edit expression]**。

   按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;按鈕以定義計算公式。

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. 選擇&#x200B;**[!UICONTROL Edit the formula using an expression]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. 在函式清單中，按兩下&#x200B;**[!UICONTROL Others]**&#x200B;節點中的&#x200B;**Iif**&#x200B;函式。

   然後在&#x200B;**[!UICONTROL Available fields]**&#x200B;部分中選擇收件人的&#x200B;**Status**。

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   輸入以下公式：**Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   此公式可讓您在狀態等於 0 時指派值為 2，而所有其他狀態的值為 4。

   按一下 **[!UICONTROL Finish]** 以核准公式。

1. 指出套用規則的期間：在此情況下為7天，以計算每週的訊息數。

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. 儲存規則以核准建立。

現在將您剛建立的規則連結至分類，以便套用至傳送。 操作步驟：

1. 建立促銷活動類型學。
1. 前往&#x200B;**[!UICONTROL Rules]**&#x200B;標籤，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並選取您剛建立的規則。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 儲存類型學：是否已新增至現有的類型清單。

若要在傳送中使用此類型，請在傳送屬性中選取它，位於&#x200B;**[!UICONTROL Typology]**&#x200B;標籤中，如下所示：

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>可以在傳遞範本中定義類型，以便自動套用至使用此範本建立的所有傳送。

在傳送分析期間，傳送收件者會視已傳送給他們的傳送數量而排除在傳送之外（如果適用）。 若要檢視此資訊，您可以：

* 查看分析結果：

   ![](assets/campaign_opt_pressure_sample_1_8.png)

* 編輯傳送，然後按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤和&#x200B;**[!UICONTROL Exclusions]**&#x200B;子標籤：

   ![](assets/campaign_opt_pressure_sample_1_9.png)

* 按一下&#x200B;**[!UICONTROL Audit]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Causes of exclusions]**&#x200B;子標籤以顯示排除數和套用的排版規則：

   ![](assets/campaign_opt_pressure_sample_1_10.png)

### 根據行為{#calculating-the-delivery-weight-based-on-behavior}計算交貨重量

您可以根據收件者行為定義壓力規則：因此，遞送的重量可以適應不同於不同接受者的標準。 例如，您可以根據收件者是否瀏覽您的網際網路網站、點選上次電子報的特定區段、訂閱資訊服務，或甚至根據調查的回答、線上遊戲等，決定傳送訊息。

在下列範例中，我們要建立重量為5的傳送。 此權重會根據收件者行為來豐富傾向分數：已從此網站訂購的客戶將獲得5分，而從未線上訂購的客戶將獲得4分。

要執行此類配置，您需要使用公式來定義消息權重。 資料模型中必須能存取傾向分數和調查答案的資訊。 在我們的範例中，已新增&#x200B;**Prodipe**&#x200B;欄位。

套用下列設定步驟：

1. 建立新的&#x200B;**Pressure**&#x200B;類型排版規則。
1. 編輯&#x200B;**[!UICONTROL Pressure]**&#x200B;標籤。 我們想要建立以每個個別收件者為基礎的臨界值公式：按一下&#x200B;**[!UICONTROL Weight formula]**&#x200B;欄位右側的&#x200B;**[!UICONTROL Edit expression]**&#x200B;表徵圖。

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. 依預設，值&#x200B;**5**&#x200B;會顯示在運算式編輯器的上方區段。 我們想要將每個收件者的傾向分數加到此權重：將游標置於5的右側，輸入&#x200B;**+**&#x200B;字元並選擇&#x200B;**傾向**&#x200B;欄位。

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. 然後，為已購買的收件者新增更高的值。 對他們來說，送貨的重量必須增加5倍，而對其他人來說，則只增加4倍。

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以儲存此規則。
1. 將規則連結至促銷活動類型學，並在傳送中參照此類型學以核准。

### 僅發送加權最高的消息{#sending-only-the-highest-weighted-messages}

您想在同一週內傳送不超過2封訊息，每天最多2封訊息給每個收件者，而且您只想要傳送具有較高權重的訊息。

為此，您需要為相同收件者排程多個具有不同權重的傳送，並套用壓力規則以排除具有較低權重的傳送。

首先，設定壓力規則。

1. 建立壓力規則。 有關詳細資訊，請參閱[建立壓力規則](#creating-a-pressure-rule)。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL Re-apply the rule at the start of personalization]**&#x200B;選項。

   ![](assets/campaign_opt_pressure_example_5.png)

   此選項會覆寫在&#x200B;**[!UICONTROL Frequency]**&#x200B;欄位中定義的值，並在個人化階段期間自動套用規則。 有關詳細資訊，請參閱[調整計算頻率](../../campaign/using/applying-rules.md#adjusting-calculation-frequency)。

1. 在&#x200B;**[!UICONTROL Pressure]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL 7d]**&#x200B;作為&#x200B;**[!UICONTROL Period considered]**，選擇&#x200B;**[!UICONTROL Grouping per day]**&#x200B;作為&#x200B;**[!UICONTROL Period type]**。
1. 選擇&#x200B;**[!UICONTROL Take the deliveries into account in the provisional calendar]**&#x200B;選項以包含已排程的傳送。

   ![](assets/campaign_opt_pressure_example_1.png)

   在計算時，會考慮到在交貨日期前7天以及預定在交貨日期後7天的交貨。 有關詳細資訊，請參閱[設定句點](#setting-the-period)。

1. 在&#x200B;**[!UICONTROL Typologies]**&#x200B;標籤中，將規則連結至促銷活動類型。
1. 儲存您的變更。

現在，針對您要套用壓力規則的每個傳送建立並設定工作流程。

1. 建立促銷活動. 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在促銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中，將&#x200B;**Query**&#x200B;活動新增至工作流程。 有關使用本練習的詳細資訊，請參閱[本節](../../workflow/using/query.md)。
1. 新增&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動至工作流程並開啟它。 有關使用本練習的詳細資訊，請參閱[本節](../../workflow/using/delivery.md)。
1. 轉至&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Approvals]**&#x200B;標籤，並停用所有核准。

   ![](assets/campaign_opt_pressure_example_2.png)

1. 在&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Typology]**&#x200B;標籤中，參考促銷活動類型學以套用規則。 定義交貨的重量。

   ![](assets/campaign_opt_pressure_example_3.png)

1. 在傳送中，按一下&#x200B;**[!UICONTROL Scheduling]**&#x200B;並選取&#x200B;**[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**。 在此示例中，選擇&#x200B;**[!UICONTROL Use a calculation formula]**&#x200B;選項。
1. 將提取日期設定為10分鐘（當前日期+ 10分鐘）。
1. 將連絡人日期設定為第二天（目前日期+ 1天）。

   ![](assets/campaign_opt_pressure_example_4.png)

   若要成功實施壓力規則排除，請務必在聯絡日期和時間之前，以及在每夜重新套用仲裁之前設定提取日期和時間。 有關詳情，請參閱[仲裁後排除](#exclusion-after-arbitration)。

1. 取消選擇&#x200B;**[!UICONTROL Confirm the delivery before sending]**&#x200B;選項並保存更改。
1. 對於您要傳送的每個傳送，請以類似方式繼續。 請確定您為每個傳送設定所需的重量。
1. 執行相關工作流程以準備和傳送傳送。

當套用夜間仲裁時，將排除相同接收者重量較低的傳送。 只有重量最高的交貨才會被考慮傳送。 有關詳細資訊，請參閱[消息權重](#message-weight)。

考慮到本週早些時候已傳送電子郵件給相關收件者，下表顯示可套用至另外兩個傳送之組態的範例。

<table> 
 <thead> 
  <tr> 
   <th> 傳送<br /> </th> 
   <th> 批准<br /> </th> 
   <th> 重量<br /> </th> 
   <th> 提取日期／時間<br /> </th> 
   <th> 聯絡日期<br /> </th> 
   <th> 傳送開始日期／時間<br /> </th> 
   <th> 仲裁工作流程執行日期／時間<br /> </th> 
   <th> 傳送狀態<br /> </th> 
   <th> 傳送（日期／時間）<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 傳送1<br /> </td> 
   <td> 已禁用<br /> </td> 
   <td> 5<br /> </td> 
   <td> 3pm<br /> </td> 
   <td> 上午8點（次日）<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> 每夜<br /> </td> 
   <td> 已排除<br /> </td> 
   <td> 已排除<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送2<br /> </td> 
   <td> 已禁用<br /> </td> 
   <td> 10<br /> </td> 
   <td> 4pm<br /> </td> 
   <td> 上午9點（次日）<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> 每夜<br /> </td> 
   <td> 已發送<br /> </td> 
   <td> 上午9點（次日）<br /> </td> 
  </tr> 
 </tbody> 
</table>

在兩個傳送的提取日期過後，在兩個傳送的聯絡日期之前重新套用夜間仲裁。 這可讓您尋找所有已傳送的傳送（已處理傳送的收件者、透過廣泛記錄記錄傳送的收件者）或計畫傳送的傳送（符合接收傳送資格的收件者，透過預測記錄記錄）。

在壓力規則中定義的時段內，所有已傳送且可能已列出傳送內容後，Adobe Campaign會依權重排序，加權最高優先。 當達到壓力規則中設定的臨界值時（此處在同一週內不超過2封電子郵件），收件者會被排除在傳送範圍之外。
