---
title: 建立協作促銷活動
seo-title: 建立協作促銷活動
description: 建立協作促銷活動
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 建立協作促銷活動{#creating-a-collaborative-campaign-intro}

中央實體會從「分散式行銷」促銷活動范 **本建立協作** 式促銷活動。 請參見[此頁面](../../campaign/using/about-distributed-marketing.md#collaborative-campaign)。

## 建立協作促銷活動 {#creating-a-collaborative-campaign}

若要設定協作促銷活動，請按一下 **[!UICONTROL Campaign management > Campaigns]** 節點，然後按一下 **[!UICONTROL New]** 圖示。

>[!NOTE]
>
>除此之 **[!UICONTROL collaborative campaigns (by campaign)]**&#x200B;外，這些促銷活動可透過網頁介面進行設定和執行。

協作促銷活動資料庫的設定程式與本機促銷活動範本的設定程式類似。 以下詳述不同類型的協作促銷活動的規格。

### 依表單 {#by-form}

若要建立協作促銷活動（依表單）, **[!UICONTROL Collaborative campaign (by form)]** 必須選取範本。

![](assets/mkg_dist_mutual_op_form2.png)

在標籤 **[!UICONTROL Edit]** 中，按一下 **[!UICONTROL Advanced campaign settings...]** 連結以存取「分 **布式行銷」標籤** 。

選擇「按 **表單** web介面」。 此類型的介面可讓您建立個人化欄位，供本機實體在訂購促銷活動時使用。 請參閱 [建立本機促銷活動（依表單）](../../campaign/using/examples.md#creating-a-local-campaign--by-form-)。

儲存促銷活動。 您現在可以從「促銷活動」 **範圍的** 「促銷活動套件」檢視中，按一下按鈕來使用它 ******[!UICONTROL Create]** 。

此檢 **[!UICONTROL Campaign Package]** 視可讓您使用本機促銷活動範本（即裝即用或複製），以及參考協作促銷活動的促銷活動，以建立不同組織實體的促銷活動。

![](assets/mkg_dist_mutual_op_form1b.png)

### 依促銷活動 {#by-campaign}

若要建立協作促銷活動（依促銷活動）, **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** 必須選取範本。

![](assets/mkg_dist_mutual_op_by_op2.png)

在排序促銷活動時，本機實體可以完成由中央實體預先定義的條件，並在排序前先評估促銷活動。

一旦中央實體核 **準（依促銷活動）** ，就會為本機實體建立子促銷活動。 當本機實體可供使用後，便可修改：

* 促銷活動工作流程，
* 排版規則，
* 個人化領域。

本機實體會執行子促銷活動。 中央實體會執行父促銷活動。

中央實體可從此控制面板（透過連結）檢視與 **Collaborative促銷活動（依促銷活動）連結的所有子****[!UICONTROL List of associated campaigns]** 促銷活動。

![](assets/mkg_dist_mutual_op_by_op.png)

### 依目標核准 {#by-target-approval}

若要建立協作促銷活動（透過目標核准）, **[!UICONTROL Collaborative campaign (by target approval)]** 必須選取範本。

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>在此模式中，中央實體不需要指定本地實體。

促銷活動工作流程必須整 **合「本機核准** 」類型活動。 活動參數如下：

* **[!UICONTROL Action to perform]** :定位核准通知。
* **[!UICONTROL Distribution context]** :明確。
* **[!UICONTROL Data distribution]** :本機實體散發。

**必須建立本地實體分佈** 類型資料分佈。 資料分發範本可讓您限制群組值清單中的記錄數。 在中 **[!UICONTROL Resources > Campaign management > Data distribution]**，按一下該 **[!UICONTROL New]** 表徵圖可建立新 **[!UICONTROL Data distribution]**。 如需資料散發的詳細資訊，請參閱「工作 [流程](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) 」指南。

![](assets/mkg_dist_data_distribution.png)

選取「 **定位** 」維度和 **[!UICONTROL Distribution field]**。 對於，選 **[!UICONTROL Assignment type]**&#x200B;擇「本 **地實體」**。

在標籤 **[!UICONTROL Distribution]** 中，為每個本機實體新增欄位並指定值。

![](assets/mkg_dist_data_distribution2.png)

您可以在「傳送類型 **」活動之** 後新增第二個Target核准 **** ，以設定報表。

在促銷活動建立通知訊息中，本機實體接收由中央實體參數預先定義的連絡人清單。

![](assets/mkg_dist_mutual_op_by_valid1.png)

本機實體可以根據促銷活動內容刪除某些連絡人。

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 簡單 {#simple}

若要建立簡單的協作促銷活動， **[!UICONTROL Collaborative campaign (simple)]** 必須選取範本。

## 建立協作促銷活動套件 {#creating-a-collaborative-campaign-package}

若要讓促銷活動可供本機實體使用，中央實體必須建立促銷活動套件。

應用以下步驟：

1. 在「促銷 **[!UICONTROL Navigation]** 活動」頁面的 **區段中** ，按一下連結 **[!UICONTROL Campaign packages]** 。
1. Click the **[!UICONTROL Create]** button.
1. 視窗頂端的區段可讓您選取范 **[!UICONTROL New collaborative package (mutualizedEmpty)]** 本。
1. 選取參考促銷活動。
1. 指定促銷活動套件的標籤、資料夾和執行排程。

### 日期 {#dates}

開始和結束日期會定義促銷活動套件清單中促銷活動的可見性時段。

對於 **協作促銷**，中央實體必須指定註冊和個人化期限。

>[!NOTE]
>
>此 **[!UICONTROL Personalization deadline]** 選項可讓中央實體選擇當地實體必須交付檔案（試算表、影像）以用於設定促銷活動的期限。 這不是強制性選項。 側移此日期不會影響促銷活動實作。

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 受眾 {#audience}

當建立協作促銷活動時，中央實體必須指定每個促銷活動涉及的本地實體。

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** 須當地相關單位指定後方可核准。

### 核准模式 {#approval-modes}

對於 **協作促銷**，您可以指定訂單核准模式。

![](assets/mkg_dist_edit_kit1.png)

在手動模式中，本機實體需要訂閱促銷活動才能參與。

在自動模式中，本機實體會預先訂閱促銷活動。 它可以取消促銷活動訂閱或修改其參數，而不需要中央實體的核准。

![](assets/mkg_dist_edit_kit2.png)

### 通知 {#notifications}

通知的設定與本機實體的通知相同。 Refer to [this section](../../campaign/using/creating-a-local-campaign.md#notifications).

## 排序促銷活動 {#ordering-a-campaign}

當協作促銷活動新增至促銷活動套件清單時，會通知屬於中央實體所定義對象的本機實體(協作促銷活動（透過目標核准） **** ，沒有預先定義的對象)。 傳送的訊息包含可讓您註冊促銷活動的連結，如下所示：

![](assets/mkg_dist_mutual_op_notification.png)

此訊息也可讓本機實體檢視建立套件的中央運算子所輸入的說明，以及連結至促銷活動的檔案。 這些項目不屬於促銷活動本身，不過它們會提供其他相關資訊。

當本機營運商透過網頁介面登入後，就可以輸入個人化資訊給他們想要訂購的協作促銷活動：

![](assets/mkg_dist_mutual_op_command.png)

當地實體完成註冊後，會以電子郵件通知中央實體核准其訂單。

![](assets/mkg_dist_mutual_op_valid_command.png)

有關詳情，請參閱「核准 [程式](../../campaign/using/creating-a-local-campaign.md#approval-process) 」一節。

## 批准訂單 {#approving-an-order}

核准協作促銷活動套件訂單的程式與核准本機促銷活動的程式相同。 Refer to [this section](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
