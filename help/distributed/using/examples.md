---
product: campaign
title: 範例
description: 範例
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 2bef6b5e-887e-4c56-bb4b-3583472ca333
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---

# 範例{#examples}

![](../../assets/v7-only.svg)

## 建立本機行銷活動（依表單） {#creating-a-local-campaign--by-form-}

**By form**&#x200B;類型的web介面涉及使用&#x200B;**web應用程式**。 此Web應用程式可包含任何類型已定義的個人化元素（視其設定而定）。 例如，您可以建議評估目標、預算、內容等的連結。 透過專用API。

>[!NOTE]
>
>API在專屬檔案中有詳細說明，其存取權取決於您的合約。 請參閱[API](../../configuration/using/about-web-services.md)。
>
>此範例中使用的Web應用程式不是隨Adobe Campaign提供而立即可用的Web應用程式。 若要在行銷活動中使用表單，您必須建立專用的Web應用程式。

建立促銷活動範本時，按一下&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;連結的&#x200B;**[!UICONTROL Web interface]**&#x200B;選項中的&#x200B;**[!UICONTROL Zoom]**&#x200B;圖示，以存取Web應用程式的詳細資訊。

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>Web應用程式參數僅可在促銷活動範本中使用。

在&#x200B;**[!UICONTROL Edit]**&#x200B;標籤中，選取&#x200B;**促銷活動順序**&#x200B;活動並開啟它以存取其內容。

![](assets/mkg_dist_web_app1.png)

在此範例中，**促銷活動順序**&#x200B;活動包括：

* 要由本地實體在訂單中輸入的欄位，

   ![](assets/mkg_dist_web_app2.png)

* 可讓本機實體評估促銷活動（例如目標、預算、內容等）的連結，

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

* 對於內容評估，

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## 建立協作行銷活動（透過目標核准） {#creating-a-collaborative-campaign--by-target-approval-}

### 簡介 {#introduction}

你是一家大型服裝品牌的營銷經理，該品牌在美國各地設有一家線上商店和幾家精品店。 春天到來了，你決定提供特惠，讓你的最好客戶將目錄中所有裙子的50%折扣。

此優惠針對的是貴機構美國門店的最佳客戶，也就是那些自年初以來已花費超過300美元的客戶。

因此，您決定使用「分散式行銷」來建立協作行銷活動（依目標核准），這可讓您選取商店的最佳客戶（依地區分組），而客戶會收到包含特殊優惠方案的電子郵件。

此範例的第一部分說明接收促銷活動建立通知的本機實體，以及他們如何使用它來評估促銷活動及排序。

此範例的第二部分說明如何建立促銷活動。

步驟如下：

**對於本地實體**

1. 使用促銷活動建立通知來存取中央實體選取的聯絡人清單。
1. 選擇聯繫人並批准參與。

**對於中央實體：**

1. 建立&#x200B;**[!UICONTROL Data distribution]**&#x200B;活動。
1. 建立協作行銷活動。
1. 發佈促銷活動。

### 本地實體側 {#local-entity-side}

1. 被選擇參與促銷活動的當地實體將收到電子郵件通知。

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. 按一下&#x200B;**[!UICONTROL Access your contact list and approve targeting]**&#x200B;連結，本機實體便可存取（透過網頁瀏覽器）為促銷活動選取的用戶端清單。

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 本地實體會從清單中取消檢查某些聯繫人，因為自年初以來，已聯繫他們以獲取類似優惠。

   ![](assets/mkg_dist_use_case_target_valid10.png)

核准檢查後，促銷活動就可以自動開始。

### 中央實體側 {#central-entity-side}

#### 建立資料分送活動 {#creating-a-data-distribution-activity}

1. 若要設定協作促銷活動（透過目標核准），您必須先建立&#x200B;**[!UICONTROL Data distribution activity]**。 按一下&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;節點中的&#x200B;**[!UICONTROL New]**&#x200B;圖示。

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，必須指定：

   * **[!UICONTROL Targeting dimension]**。 在此，在&#x200B;**Recipients**&#x200B;上執行&#x200B;**資料分發**。
   * **[!UICONTROL Distribution type]**。 您可以選擇&#x200B;**固定大小**&#x200B;或&#x200B;**大小作為百分比**。
   * **[!UICONTROL Assignment type]**。 選擇&#x200B;**本地實體**&#x200B;選項。
   * **[!UICONTROL Distribution type]**。 在此，收件者表格中顯示的&#x200B;**[!UICONTROL Origin (@origin)]**&#x200B;欄位可讓您識別聯絡人與本機實體之間的關係。
   * **[!UICONTROL Approval storage]**&#x200B;欄位。 選擇&#x200B;**收件者的本地批准**&#x200B;選項。

1. 在&#x200B;**[!UICONTROL Breakdown]**&#x200B;標籤中，指定：

   * **[!UICONTROL Distribution field value]**，與即將進行之促銷活動涉及的當地實體相對應。
   * 本地實體&#x200B;**[!UICONTROL label]**。
   * **[!UICONTROL Size]**（固定或百分比）。 **0預設值**&#x200B;涉及選擇連結到本地實體的所有收件人。

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 儲存新的資料分送。

#### 建立協作行銷活動 {#creating-a-collaborative-campaign}

1. 從&#x200B;**[!UICONTROL Campaign management > Campaign]**&#x200B;節點建立新的&#x200B;**[!UICONTROL collaborative campaign (by target approval)]**。
1. 在&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中，建立促銷活動的工作流程。 這必須包含&#x200B;**Split**&#x200B;活動，其中&#x200B;**[!UICONTROL Record count limitation]**&#x200B;由&#x200B;**[!UICONTROL Data distribution]**&#x200B;活動定義。

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 新增&#x200B;**[!UICONTROL Local approval]**&#x200B;動作，您可在其中指定：

   * 將發送到通知中的本地實體的消息內容，
   * 批准提醒，
   * 預期的促銷活動處理。

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 保存您的記錄。

#### 發佈行銷活動 {#publishing-the-campaign}

您現在可以從&#x200B;**[!UICONTROL Campaigns]**&#x200B;標籤新增&#x200B;**促銷活動套件**。

1. 選擇您的&#x200B;**[!UICONTROL Reference campaign]**。 在套件的&#x200B;**[!UICONTROL Edit]**&#x200B;標籤中，您可以選取要用於促銷活動的&#x200B;**[!UICONTROL Approval mode]**:

   * 在&#x200B;**手動**&#x200B;模式中，如果本地實體接受中央實體的邀請，則它們將參與促銷活動。 如果他們想要，則可以刪除預先選擇的聯繫人，並且需要經理的批准才能確認他們參與促銷活動。
   * 在&#x200B;**自動**&#x200B;模式中，除非本地實體從中註銷自己，否則本地實體必須參與促銷活動。 他們可以刪除聯繫人，無需批准。

   ![](assets/mkg_dist_use_case_target_valid.png)

1. 在&#x200B;**[!UICONTROL Description]**&#x200B;標籤中，您可以新增行銷活動的說明，以及要傳送至本機實體的任何檔案。

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 核准您的促銷活動套件，然後開始您的工作流程以發佈套件，並讓套件清單中的所有本機實體都能使用。

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 建立協作行銷活動（依表單） {#creating-a-collaborative-campaign--by-form-}

### 簡介 {#introduction-1}

你是一家大型化妝品品牌的營銷經理，該品牌在美國各地設有一家線上商店和幾家精品店。 要卸載冬季庫存並為新庫存騰出空間，您決定建立以兩個客戶類別為目標的特殊優惠方案：30歲以上的人，你將向他們提供年齡敏感的護膚產品，30歲以下的人，你將向他們提供更基本的護膚產品。

因此，您決定使用「分散式行銷」來建立協作行銷活動（依表單），讓您能夠依年齡範圍從不同商店選取客戶。 這些客戶會收到電子郵件傳送，其中包含根據年齡範圍個人化的特殊優惠方案。

此範例的第一部分說明接收促銷活動建立通知的本機實體，以及他們如何使用它來評估促銷活動及排序。

此範例的第二部分說明如何建立促銷活動。

步驟如下：

**對於本地實體**

1. 使用促銷活動建立通知來存取線上表單。
1. 個人化促銷活動（目標、內容、傳送量）。
1. 檢查這些欄位，並視需要加以變更。
1. 核准您的參與。
1. 本機實體（或中央實體）的管理員會核准您的設定和參與。

**對於中央實體：**

1. 建立協作行銷活動。
1. 如您對本機促銷活動所設定的&#x200B;**[!UICONTROL Advanced campaign settings...]**。
1. 如您對本機促銷活動所設定的，設定促銷活動工作流程和傳送。
1. 更新Web表單。
1. 建立行銷活動套件並發佈。

### 本地實體側 {#local-entity-side-1}

1. 選擇參與促銷活動的當地實體會收到電子郵件通知，通知他們參與促銷活動。

   ![](assets/mkg_dist_use_case_form_7.png)

1. 當地實體會完成個人化表單，然後：

   * 評估目標和預算，
   * 預覽傳遞內容，
   * 核准其參與。

      ![](assets/mkg_dist_use_case_form_8.png)

1. 負責驗證訂單的操作員批准其參與。

   ![](assets/mkg_dist_use_case_form_9.png)

### 中央實體側 {#central-entity-side-1}

1. 若要實作協作促銷活動（依表單），您必須使用&#x200B;**協作促銷活動（依表單）**&#x200B;範本建立促銷活動。

   ![](assets/mkg_dist_use_case_form_1.png)

1. 在促銷活動的&#x200B;**[!UICONTROL Edit]**&#x200B;標籤中，按一下&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;連結，將其設為本機促銷活動。 請參閱[建立本機促銷活動（依表單）](#creating-a-local-campaign--by-form-)。

   ![](assets/mkg_dist_use_case_form_2.png)

1. 設定促銷活動工作流程和網頁表單。 請參閱[建立本機促銷活動（依表單）](#creating-a-local-campaign--by-form-)。
1. 指定執行排程和相關的本機實體，以建立您的促銷活動套件。

   ![](assets/mkg_dist_use_case_form_3.png)

1. 在&#x200B;**[!UICONTROL Edit]**&#x200B;標籤中選取核准模式，以完成套件設定。

   ![](assets/mkg_dist_use_case_form_4.png)

1. 從&#x200B;**[!UICONTROL Description]**&#x200B;標籤，您可以輸入促銷活動套件說明、發佈套件時要傳送至本機實體的通知訊息，以及將任何資訊性檔案附加至您的促銷活動套件。

   ![](assets/mkg_dist_use_case_form_5.png)

1. 核准套件以發佈。

   ![](assets/mkg_dist_use_case_form_6.png)