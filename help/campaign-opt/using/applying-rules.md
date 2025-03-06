---
product: campaign
title: 套用型別規則
description: 瞭解如何套用型別規則
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: 09ec0fc0-76ed-4c73-8bdf-c931e2103aa9
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 8%

---

# 套用型別規則{#applying-rules}

## 將型別套用至傳遞 {#applying-a-typology-to-a-delivery}

若要套用您建立的型別規則，您必須將其與型別建立關聯，然後在傳送中參考此型別。 操作步驟：

1. 建立行銷活動型別。

   可透過&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;節點存取型別。

1. 移至&#x200B;**[!UICONTROL Rules]**&#x200B;標籤，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後選取要套用至此型別的規則。

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 儲存型別：會將其新增至現有型別的清單中。
1. 開啟您要套用規則的傳送。
1. 開啟傳遞屬性並存取&#x200B;**[!UICONTROL Typology]**&#x200B;標籤。
1. 在下拉式清單中選取型別。

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >可以在傳遞範本中定義類型，以便自動套用至使用此範本建立的所有傳送。

## 定義應用程式條件 {#defining-application-conditions}

您可以視需要限制規則的應用程式欄位（控制規則除外）。

您可以設定型別規則，使其僅涉及所連結的特定傳遞，或傳遞目標中的特定收件者。

若要定義規則的應用程式條件，請按一下&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中的&#x200B;**[!UICONTROL Edit the rule application conditions...]**&#x200B;連結。

然後使用查詢編輯器來定義篩選條件。 在以下範例中，容量規則僅涉及標籤中包含「offer」字樣的傳送，或是在2013年4月1日之前建立的傳送。

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>對於篩選規則，您可以選取篩選條件的套用條件：這些條件取決於傳遞或傳遞大網。 如需詳細資訊，請參閱[設定篩選規則](filtering-rules.md#conditioning-a-filtering-rule)。

## 調整計算頻率 {#adjusting-calculation-frequency}

仲裁會透過資料庫清理工作流程每晚自動重新執行。 不過，在此期間之後可儲存值。

事實上，有些計算使用的值不會每日變更。 因此，每天重新計算資料且讓資料庫過載毫無意義無關緊要。 例如，如果流程每週都透過客戶傾向分數和購買資訊來豐富行銷資料庫，則不需要每天重新計算基於這些值的資料。

若要這麼做，**[!UICONTROL General]**&#x200B;索引標籤的&#x200B;**[!UICONTROL Frequency]**&#x200B;欄位可讓您定義儲存定位的最長時段。 根據預設，值&#x200B;**0**&#x200B;表示在下次執行每日重新仲裁之前，計算仍然有效。

若要儲存超過此期間的結果，請在&#x200B;**[!UICONTROL Frequency]**&#x200B;欄位中輸入大於12的值：一旦此期間到期，就會重新套用所有規則。

**[!UICONTROL Re-apply the rule at the start of personalization]**&#x200B;選項可讓您在個人化階段期間自動套用規則，包括&#x200B;**[!UICONTROL Frequency]**&#x200B;欄位中所述的期間是否仍然有效。

## 選取規則應用程式階段 {#selecting-the-rule-application-phase}

型別規則會在其關注之傳遞的目標定位、分析和個人化階段中，以特定順序套用。

### 執行順序 {#execution-order}

在標準操作模式下，會依下列順序套用規則：

1. 控制規則（如果這些規則是在定位開始時套用）。
1. 篩選規則：

   * 位址限定的原生應用程式規則：封鎖清單/隔離位址/位址品質上已定義的位址/未驗證的位址/位址。
   * 篩選由使用者定義的規則。
   * 地址或識別碼上的重複資料刪除規則（必要時套用）。

1. 壓力規則。
1. 容量規則。
1. 控制規則（如果這些規則是在定位結束時套用）。
1. 控制規則（如果這些規則是在個人化開始時套用）。 如果使用者規則（篩選/壓力/電容）已過期且需要重新計算，則將在這個步驟中套用這些規則。
1. 控制規則（如果這些規則是在個人化結束時套用）。

>[!NOTE]
>
>如果您使用Campaign互動模組，優惠方案適用性規則會在篩選規則（適用於傳遞大網中的優惠方案）或個人化階段期間（呼叫優惠方案引擎期間）套用。

您可以使用規則&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中的適當欄位，調整具有相同型別的規則執行順序。 在相同的訊息處理階段期間執行數個規則時，您可以在&#x200B;**[!UICONTROL Execution sequence]**&#x200B;欄位中設定其執行順序。

例如，執行順序為20的壓力規則將在執行順序為30的壓力規則之前執行。

### 控制規則 {#control-rules}

對於&#x200B;**[!UICONTROL Control]**&#x200B;個規則，您可以決定要在傳遞生命週期的哪個時間點套用規則（在鎖定目標之前或之後、在個人化開始時、在分析結束時）。 在型別規則的&#x200B;**[!UICONTROL General]**&#x200B;索引標籤的&#x200B;**[!UICONTROL Phase]**&#x200B;欄位下拉式清單中，選取要套用的值。

![](assets/campaign_opt_define_control_phase.png)

可能的值包括：

* **[!UICONTROL At the start of targeting]**

  若要防止在發生錯誤時執行個人化步驟，您可以在此處套用控制規則。

* **[!UICONTROL After targeting]**

  如果您需要知道目標的音量以套用控制規則，請選取此階段。

  例如，**[!UICONTROL Check proof size]**&#x200B;控制規則會在每個目標階段之後套用：如果校樣收件者過多，此規則會防止訊息個人化。

* **[!UICONTROL At the start of personalization]**

  如果控制涉及核准訊息個人化，則必須選取此階段。 訊息個人化會在分析階段中執行。

* **[!UICONTROL At the end of the analysis]**

  當檢查要求完成訊息個人化時，請選取此階段。

## 其他設定 {#additional-configurations}

### 控制傳出SMTP流量 {#control-outgoing-smtp-traffic}

您可以選擇使用&#x200B;**[!UICONTROL Managing affinities with IP addresses]**&#x200B;欄位，將傳遞連結至傳遞伺服器(MTA)。 這可讓您限制特定傳遞至機器或輸出地址的電子郵件數量。

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>相似性管理不適用於&#x200B;**[!UICONTROL Filtering]**&#x200B;型別。\
>相關性是在Adobe Campaign伺服器的執行個體設定檔案中定義。 如需詳細資訊，請參閱[本章節](../../installation/using/about-initial-configuration.md)。

### 行銷活動最佳化和分散式行銷 {#campaign-optimization-and-distributed-marketing}

**[!UICONTROL Distributed Marketing]**&#x200B;索引標籤可讓您定義重新對應型別和/或規則，以便在訂購和/或保留共用行銷活動時套用。 為本機實體定義的型別/規則（連結至為中央實體定義的型別/規則）會取代連結至中央實體的規則/型別。 重新對應可讓您將中央實體規則調整為適合訂購行銷活動的本地實體。

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>在型別與型別規則中，如果您的授權包含此選項，則會新增&#x200B;**[!UICONTROL Distributed Marketing]**&#x200B;標籤：請檢查您的授權合約。\
>如需分散式行銷的詳細資訊，請參閱[關於分散式行銷](../../distributed/using/about-distributed-marketing.md)。
