---
title: 範例
seo-title: 範例
description: 範例
seo-description: null
page-status-flag: never-activated
uuid: bfc9bb13-500b-4435-b56a-550588a240bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 7b0aef75-345d-45be-b7d0-a9f6944ee678
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eee744eb5bc7a43fd412ffb01f0546385146a978

---


# 範例{#examples}

## 建立本機促銷活動（依表單） {#creating-a-local-campaign--by-form-}

By表 **單類型** Web介面涉及使用 **Web應用程式**。 此Web應用程式可包含任何類型已定義的個人化元素，視其設定而定。 例如，您可以建議連結來評估目標、預算、內容等。 透過專屬API。

>[!NOTE]
>
>API會在專屬檔案中詳細列出，其存取權取決於您的合約。 請參閱 [API](../../configuration/using/about-web-services.md)。
>
>此範例中使用的網頁應用程式並非隨附Adobe Campaign而現成的網頁應用程式。 若要在促銷活動中使用表單，您必須建立專用的Web應用程式。

建立促銷活動範本時，按一 **[!UICONTROL Zoom]** 下連結選項中 **[!UICONTROL Web interface]** 的圖 **[!UICONTROL Advanced campaign settings...]** 示，以存取Web應用程式的詳細資訊。

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>Web應用程式參數僅適用於促銷活動範本。

在標籤 **[!UICONTROL Edit]** 中，選取「促銷 **活動」訂單活動** ，並開啟它以存取其內容。

![](assets/mkg_dist_web_app1.png)

在此範例中，促銷活 **動訂單活動** 包括：

* 欄位，

   ![](assets/mkg_dist_web_app2.png)

* 可讓本機實體評估促銷活動的連結（例如目標、預算、內容等）,

   ![](assets/mkg_dist_web_app3.png)

* 可讓您計算和顯示這些評估結果的指令碼。

   ![](assets/mkg_dist_web_app4.png)

在此範例中，會使用下列API:

* 對於目標評估，

   ```
   var res = nms.localOrder.EvaluateTarget(ctx.localOrder);
   ```

* 對於預算評估，

   ```
   var res = nms.localOrder.EvaluateDeliveryBudget(ctx.@deliveryId, NL.XTK.parseNumber(ctx.@compt));
   ```

* 內容評估，

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## 建立協作促銷活動（透過目標核准） {#creating-a-collaborative-campaign--by-target-approval-}

### 簡介 {#introduction}

你是一家大型服裝品牌的營銷經理，該品牌在美國各地擁有一家線上商店和幾家精品店。 現在春天到來了，你決定推出一個特惠方案，讓你的最佳客戶能享有您目錄中所有服飾50%的折扣。

此優惠針對的是您美國商店的最佳客戶，即自年初以來已花費超過300美元的客戶。

因此，您決定使用「分散式行銷」來建立協作促銷活動（透過目標核准），讓您選擇您商店的最佳客戶（依地區分組），這些客戶將會收到包含特殊優惠的電子郵件傳送。

此範例的第一部分說明接收促銷活動建立通知的本機實體，以及他們如何使用它來評估促銷活動並排序。

此範例的第二部分說明如何建立促銷活動。

步驟如下：

**對於本地實體**

1. 使用促銷活動建立通知來存取中央實體選取的聯絡人清單。
1. 選擇聯繫人並批准參與。

**對於中央實體：**

1. 建立活 **[!UICONTROL Data distribution]** 動。
1. 建立協作促銷活動。
1. 發佈促銷活動。

### 本端實體側 {#local-entity-side}

1. 已選擇參與促銷活動的當地實體將會收到電子郵件通知。

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. 按一下連 **[!UICONTROL Access your contact list and approve targeting]** 結，即可（透過網頁瀏覽器）存取為促銷活動選取的用戶端清單。

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 當地實體會從清單中取消勾選某些連絡人，因為自年初以來，已與他們聯絡以取得類似的選件。

   ![](assets/mkg_dist_use_case_target_valid10.png)

一旦核准檢查後，促銷活動就會自動啟動。

### 中央實體側 {#central-entity-side}

#### 建立資料分發活動 {#creating-a-data-distribution-activity}

1. 若要設定協作促銷活動（透過目標核准），您必須先建立 **[!UICONTROL Data distribution activity]**。 按一下節 **[!UICONTROL New]** 點中的圖 **[!UICONTROL Resources > Campaign management > Data distribution]** 標。

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. 在標籤 **[!UICONTROL General]** 中，您必須指定：

   * the **[!UICONTROL Targeting dimension]**&#x200B;在此， **資料分發** 會對收件者 **執行**。
   * the **[!UICONTROL Distribution type]**&#x200B;您可以選擇「固 **定大小** 」或「 **大小」作為百分比**。
   * the **[!UICONTROL Assignment type]**&#x200B;選擇「本 **地實體** 」選項。
   * the **[!UICONTROL Distribution type]**&#x200B;在此，「收件者」 **[!UICONTROL Origin (@origin)]** 表格中顯示的欄位可讓您識別聯繫人與本機實體之間的關係。
   * 欄 **[!UICONTROL Approval storage]** 位。 選擇「收 **件者的本地批准** 」選項。

1. 在標籤 **[!UICONTROL Breakdown]** 中，指定：

   * 的 **[!UICONTROL Distribution field value]**&#x200B;值，此值對應於參與即將進行之促銷活動的當地實體。
   * 本機實體 **[!UICONTROL label]**。
   * ( **[!UICONTROL Size]** 固定或百分比)。 0的 **預設值** ，包括選取連結至本機實體的所有收件者。
   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 儲存您的新資料分發。

#### 建立協作促銷活動 {#creating-a-collaborative-campaign}

1. 從節 **[!UICONTROL Campaign management > Campaign]** 點建立新 **[!UICONTROL collaborative campaign (by target approval)]**。
1. 在標籤 **[!UICONTROL Targeting and workflows]** 中，建立促銷活動的工作流程。 這必須包含 **Split** 活動，活動 **[!UICONTROL Record count limitation]** 在其中定 **[!UICONTROL Data distribution]** 義。

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 新增可 **[!UICONTROL Local approval]** 指定的動作：

   * 即會傳送給通知中本機實體的訊息內容，
   * 核准提醒，
   * 促銷活動的預期處理。
   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 儲存您的記錄。

#### 發佈促銷活動 {#publishing-the-campaign}

您現在可以從「促銷活 **動」範圍** ，新增 **促銷活動** 套件。

1. 選擇您的 **[!UICONTROL Reference campaign]**。 在套件 **[!UICONTROL Edit]** 的標籤中，您可以選取要用 **[!UICONTROL Approval mode]** 於促銷活動的：

   * 在「 **手動** 」模式中，如果本地實體接受中央實體的邀請，就會參與促銷活動。 如果他們想要，而且必須向經理核准，才能確認其參與促銷活動，他們可以刪除預先選取的聯絡人。
   * 在「 **自動** 」模式中，除非本地實體從中註銷，否則必須參與促銷活動。 他們可以刪除聯絡人，而不需要核准。
   ![](assets/mkg_dist_use_case_target_valid.png)

1. 在標籤 **[!UICONTROL Description]** 中，您可以新增促銷活動的說明，以及任何要傳送至本機實體的檔案。

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 核准您的促銷活動套件，然後啟動您的工作流程來發佈套件，並將它提供給套件清單中的所有本機實體。

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 建立協作促銷活動（依表單） {#creating-a-collaborative-campaign--by-form-}

### 簡介 {#introduction-1}

你是一家大型化妝品品牌的營銷經理，該品牌在美國各地擁有一家線上商店和幾家精品店。 若要卸載冬季庫存並騰出空間供新庫存使用，您決定建立特殊選件，以鎖定兩個客戶類別：30歲以上的人，將向他們提供年齡敏感的護膚產品，以及30歲以下的人，將向他們提供更基本的護膚產品。

因此，您決定使用「分佈式行銷」來建立協作促銷活動（依表單），讓您可以依年齡範圍從不同商店選擇客戶。 這些客戶將會收到電子郵件，其特別優惠會根據其年齡範圍進行個人化。

此範例的第一部分說明接收促銷活動建立通知的本機實體，以及他們如何使用它來評估促銷活動並排序。

此範例的第二部分說明如何建立促銷活動。

步驟如下：

**對於本地實體**

1. 使用促銷活動建立通知來存取線上表單。
1. 個人化促銷活動（目標、內容、傳送量）。
1. 請勾選這些欄位，並視需要變更欄位。
1. 核准您的參與。
1. 本機實體（或中央實體）的經理會核准您的設定和參與。

**對於中央實體：**

1. 建立協作促銷活動。
1. 設定本 **[!UICONTROL Advanced campaign settings...]** 機促銷活動的方式。
1. 設定促銷活動工作流程和傳送方式，就像您對本機促銷活動一樣。
1. 更新Web表格。
1. 建立促銷活動套件並發佈。

### 本端實體側 {#local-entity-side-1}

1. 選擇參與促銷活動的本機實體會收到電子郵件通知，通知他們參與促銷活動。

   ![](assets/mkg_dist_use_case_form_7.png)

1. 當地實體完成個性化表單，然後：

   * 評估目標和預算，
   * 預覽傳送內容，
   * 核准其參與率。

      ![](assets/mkg_dist_use_case_form_8.png)

1. 負責驗證訂單的營運商會核准其參與。

   ![](assets/mkg_dist_use_case_form_9.png)

### 中央實體側 {#central-entity-side-1}

1. 若要實作協作促銷活動（依表單），您必須使用「協作促銷活動」（依表單）范 **本建立促銷活動** 。

   ![](assets/mkg_dist_use_case_form_1.png)

1. 在促銷活動的標 **[!UICONTROL Edit]** 簽中，按一下 **[!UICONTROL Advanced campaign settings...]** 連結，將其設定為本機促銷活動。 請參閱 [建立本機促銷活動（依表單）](#creating-a-local-campaign--by-form-)。

   ![](assets/mkg_dist_use_case_form_2.png)

1. 設定促銷活動工作流程和Web表單。 請參閱 [建立本機促銷活動（依表單）](#creating-a-local-campaign--by-form-)。
1. 指定執行排程和相關的本機實體，以建立促銷活動套件。

   ![](assets/mkg_dist_use_case_form_3.png)

1. 通過在頁籤中選擇批准模式來最終確定包 **[!UICONTROL Edit]** 配置。

   ![](assets/mkg_dist_use_case_form_4.png)

1. 在標籤 **[!UICONTROL Description]** 中，您可以輸入促銷活動套件說明、發佈套件時要傳送至本機實體的通知訊息，以及將任何資訊性檔案附加至您的促銷活動套件。

   ![](assets/mkg_dist_use_case_form_5.png)

1. 批准套件以發佈。

   ![](assets/mkg_dist_use_case_form_6.png)

