---
solution: Campaign Classic
product: campaign
title: 套用規則
description: 套用規則
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 9%

---


# 套用規則{#applying-rules}

## 套用類型學至遞送{#applying-a-typology-to-a-delivery}

若要套用您建立的排版規則，您必須將其與排版學建立關聯，然後在傳送時參照此排版學。 操作步驟：

1. 建立促銷活動類型學。

   通過&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;節點訪問類型。

1. 前往&#x200B;**[!UICONTROL Rules]**&#x200B;標籤，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，並選取要套用此類型的規則。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 儲存類型學：是否已新增至現有的類型清單。
1. 開啟您要套用規則的傳送。
1. 開啟傳送屬性並存取&#x200B;**[!UICONTROL Typology]**&#x200B;標籤。
1. 在下拉式清單中選取類型學。

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >可以在傳遞範本中定義類型，以便自動套用至使用此範本建立的所有傳送。

## 定義應用程式條件{#defining-application-conditions}

您可以根據需要限制規則的應用程式欄位（控制規則除外）。

您可以設定排版規則，使其僅關注其連結的特定傳送，或某些收件者屬於傳送目標。

要定義規則的應用條件，請按一下&#x200B;**[!UICONTROL General]**&#x200B;頁籤中的&#x200B;**[!UICONTROL Edit the rule application conditions...]**&#x200B;連結。

然後使用查詢編輯器來定義篩選條件。 在下例中，容量規則僅涉及標籤中含有「選件」字樣的交貨，或2013年4月1日之前建立的交貨。

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>對於篩選規則，您可以選擇篩選條件的應用條件：它們可以依賴傳送或傳送大綱。 有關詳細資訊，請參閱[ Conditioning a filtering rule](../../campaign/using/filtering-rules.md#conditioning-a-filtering-rule)。

## 調整計算頻率{#adjusting-calculation-frequency}

通過資料庫清理工作流程，每天晚上自動重新執行仲裁。 不過，值可儲存在此期間之後。

事實上，有些計算使用的值並不會每日改變。 因此，每天重新計算資料並不重要，而是讓資料庫無所謂地過載。 例如，如果流程以每週客戶傾向分數和購買資訊豐富行銷資料庫，則不需要每天重新計算以這些值為基礎的資料。

為此，**[!UICONTROL General]**&#x200B;標籤的&#x200B;**[!UICONTROL Frequency]**&#x200B;欄位可讓您定義儲存定位的最大期間。 預設情況下，值&#x200B;**0**&#x200B;表示計算在下次執行每日重新仲裁之前保持有效。

要保存超過此期間的結果，請在&#x200B;**[!UICONTROL Frequency]**&#x200B;欄位中輸入大於12的值：一旦此期間過期，就會重新套用所有規則。

**[!UICONTROL Re-apply the rule at the start of personalization]**&#x200B;選項可讓您在個人化階段自動套用規則，包括如果&#x200B;**[!UICONTROL Frequency]**&#x200B;欄位中指明的期間仍然有效。

## 選擇規則應用程式階段{#selecting-the-rule-application-phase}

在其所關注之遞送的定位、分析和個人化階段，分類規則會套用在特定序列中。

### 執行順序{#execution-order}

在標準操作模式下，會依下列順序套用規則：

1. 控制規則（如果這些規則是在定位開始時套用）。
1. 篩選規則：

   * 地址限定的原生應用程式規則：denylist /隔離地址／地址質量上的已定義地址／未驗證地址／地址。
   * 篩選由使用者定義的規則。
   * 位址或識別碼的去重複化規則（視需要套用）。

1. 壓力規則.
1. 容量規則。
1. 控制規則（如果這些規則是在定位結束時套用）。
1. 控制規則（如果這些規則是在個人化開始時套用）。如果使用者規則（篩選／壓力／容性）已過期，需要重新計算，則會在此步驟中套用。
1. 控制規則（如果規則在個人化結束時套用）。

>[!NOTE]
>
>如果您使用「促銷活動互動」模組，則在呼叫選件引擎期間，選件資格規則會與篩選規則（在傳送大綱中找到的選件）或在個人化階段中套用。

您可以使用規則的&#x200B;**[!UICONTROL General]**&#x200B;標籤中的適當欄位，來調整具有相同類型的規則的執行順序。 當在相同的消息處理階段中執行多個規則時，您可以在&#x200B;**[!UICONTROL Execution sequence]**&#x200B;欄位中設定其執行順序。

例如，執行順序為20的壓力規則在執行順序為30的壓力規則之前執行。

### 控制規則 {#control-rules}

對於&#x200B;**[!UICONTROL Control]**&#x200B;規則，您可以決定將套用規則的傳送生命週期的哪個點（在定位之前或之後，在個人化開始時，在分析結束時）。 在&#x200B;**[!UICONTROL Phase]**&#x200B;欄位的下拉式清單中，選取要套用的值，位於排版規則的&#x200B;**[!UICONTROL General]**&#x200B;標籤中。

![](assets/campaign_opt_define_control_phase.png)

可能的值包括：

* **[!UICONTROL At the start of targeting]**

   若要防止在發生錯誤時執行個人化步驟，您可以在此處套用控制規則。

* **[!UICONTROL After targeting]**

   如果您需要知道目標的卷才能應用控制規則，請選擇此階段。

   例如，**[!UICONTROL Check proof size]**&#x200B;控制規則會套用至每個定位階段之後：如果有太多的證明收件者，此規則可防止訊息個人化。

* **[!UICONTROL At the start of personalization]**

   如果控制項與訊息個人化的核准有關，則必須選取此階段。 在分析階段中執行消息個性化。

* **[!UICONTROL At the end of the analysis]**

   當檢查要求消息個性化完成時，請選擇此階段。

## 其他配置 {#additional-configurations}

### 控制傳出SMTP通信{#control-outgoing-smtp-traffic}

選項是，您可以使用&#x200B;**[!UICONTROL Managing affinities with IP addresses]**&#x200B;欄位將傳送連結至傳送伺服器(MTA)。 這可讓您限制特定傳送給電腦或輸出地址的電子郵件數。

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>相似性管理不適用於&#x200B;**[!UICONTROL Filtering]**&#x200B;類型。\
>相關性是在Adobe Campaign伺服器的例項設定檔案中定義。 如需詳細資訊，請參閱[本章節](../../installation/using/about-initial-configuration.md)。

### 促銷活動最佳化與分散式行銷{#campaign-optimization-and-distributed-marketing}

**[!UICONTROL Distributed Marketing]**&#x200B;標籤可讓您定義在訂購和／或保留共用促銷活動時套用的類型和／或規則的重新對應。 為本地實體定義的類型／規則（與為中央實體定義的類型相連結）將替換與中央實體連結的規則／類型。 重新對應可讓您將中央實體規則調整至訂購促銷活動的本機實體。

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>在類型和類型規則中，如果您的授權包含下列選項，則會新增&#x200B;**[!UICONTROL Distributed Marketing]**&#x200B;標籤：請檢查您的授權合約。\
>有關Distributed Marketing的詳細資訊，請參閱[關於Distributed Marketing](../../campaign/using/about-distributed-marketing.md)。

