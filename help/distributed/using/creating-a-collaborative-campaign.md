---
product: campaign
title: 建立協作行銷活動
description: 瞭解如何建立合作行銷活動
feature: Distributed Marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 4%

---

# 建立協作行銷活動{#creating-a-collaborative-campaign-intro}



中央實體會從&#x200B;**分散式行銷**&#x200B;行銷活動範本建立合作行銷活動。 請參見[此頁面](about-distributed-marketing.md#collaborative-campaign)。

## 建立協作行銷活動 {#creating-a-collaborative-campaign}

若要設定合作行銷活動，請按一下&#x200B;**[!UICONTROL Campaign management > Campaigns]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL New]**&#x200B;圖示。

>[!NOTE]
>
>除了&#x200B;**[!UICONTROL collaborative campaigns (by campaign)]**，這些行銷活動也可以透過網頁介面設定及執行。

合作行銷活動資料庫的設定程式與本機行銷活動範本的設定程式類似。 不同型別的合作行銷活動的規格詳述如下。

### 依表單 {#by-form}

若要建立合作行銷活動（依表單），必須選取&#x200B;**[!UICONTROL Collaborative campaign (by form)]**&#x200B;範本。

![](assets/mkg_dist_mutual_op_form2.png)

在&#x200B;**[!UICONTROL Edit]**&#x200B;標籤中，按一下&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;連結以存取&#x200B;**分散式行銷**&#x200B;標籤。

選取&#x200B;**By form**&#x200B;網頁介面。 此型別的介面可讓您建立個人化欄位，本機實體在訂購行銷活動時會使用這些欄位。 請參閱[建立本機行銷活動（依表單）](examples.md#creating-a-local-campaign--by-form-)。

儲存您的行銷活動。 您現在可以從&#x200B;**行銷活動**&#x200B;索引標籤中的&#x200B;**行銷活動套件**&#x200B;檢視，按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕來使用它。

**[!UICONTROL Campaign Package]**&#x200B;檢視可讓您使用本機行銷活動範本（現成或重複），以及合作行銷活動的參考行銷活動，目標是為您不同的組織實體建立行銷活動。

![](assets/mkg_dist_mutual_op_form1b.png)

### 依行銷活動 {#by-campaign}

若要建立合作行銷活動（依行銷活動），必須選取&#x200B;**[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]**&#x200B;範本。

![](assets/mkg_dist_mutual_op_by_op2.png)

訂購行銷活動時，本機實體可完成中央實體預先定義的條件，並在訂購行銷活動之前評估行銷活動。

中央實體核准&#x200B;**合作行銷活動（依行銷活動）**&#x200B;的訂單後，就會為本機實體建立子行銷活動。 一旦可供他們使用，本機實體就可以修改：

* 行銷活動工作流程，
* 型別規則，
* 和個人化欄位。

本機實體會執行子行銷活動。 中央實體執行父級行銷活動。

中央實體可從此儀表板（透過&#x200B;**[!UICONTROL List of associated campaigns]**&#x200B;連結）檢視與&#x200B;**合作行銷活動（依行銷活動）**&#x200B;連結的所有子行銷活動。

![](assets/mkg_dist_mutual_op_by_op.png)

### 依據目標核准 {#by-target-approval}

若要建立合作行銷活動（依目標核准），必須選取&#x200B;**[!UICONTROL Collaborative campaign (by target approval)]**&#x200B;範本。

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>在此模式中，中央實體不需要指定本機實體。

行銷活動工作流程必須整合&#x200B;**本機核准**&#x200B;型別活動。 活動引數如下：

* **[!UICONTROL Action to perform]** ：目標核准通知。
* **[!UICONTROL Distribution context]** ：明確。
* **[!UICONTROL Data distribution]** ：本機實體發佈。

必須建立&#x200B;**本機實體發佈**&#x200B;型別資料發佈。 資料分佈範本可讓您限制分組值清單中的記錄數。 在&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;中，按一下&#x200B;**[!UICONTROL New]**&#x200B;圖示以建立新的&#x200B;**[!UICONTROL Data distribution]**。 如需資料分配的詳細資訊，請參閱[工作流程](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-)指南。

![](assets/mkg_dist_data_distribution.png)

選取&#x200B;**目標維度**&#x200B;和&#x200B;**[!UICONTROL Distribution field]**。 針對&#x200B;**[!UICONTROL Assignment type]**，選取&#x200B;**本機實體**。

在&#x200B;**[!UICONTROL Distribution]**&#x200B;索引標籤中，為每個本機實體新增欄位並指定值。

![](assets/mkg_dist_data_distribution2.png)

您可以在&#x200B;**傳遞**&#x200B;型別活動之後新增第二個&#x200B;**目標核准**，以設定其上的報告。

在行銷活動建立通知訊息中，本機實體會接收已由中央實體引數預先定義的聯絡人清單。

![](assets/mkg_dist_mutual_op_by_valid1.png)

本機實體可以根據行銷活動內容刪除某些聯絡人。

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 簡單 {#simple}

若要建立簡單的合作行銷活動，必須選取&#x200B;**[!UICONTROL Collaborative campaign (simple)]**&#x200B;範本。

## 建立合作行銷活動套件 {#creating-a-collaborative-campaign-package}

若要讓本機實體可使用行銷活動，中央實體必須建立行銷活動套件。

應用以下步驟：

1. 在&#x200B;**行銷活動**&#x200B;頁面的&#x200B;**[!UICONTROL Navigation]**&#x200B;區段中，按一下&#x200B;**[!UICONTROL Campaign packages]**&#x200B;連結。
1. 按一下 **[!UICONTROL Create]** 按鈕。
1. 視窗頂端的區段可讓您選取&#x200B;**[!UICONTROL New collaborative package (mutualizedEmpty)]**&#x200B;範本。
1. 選取參考行銷活動。
1. 指定行銷活動套件的標籤、資料夾和執行排程。

### 日期 {#dates}

開始和結束日期定義行銷活動套件清單中的行銷活動可見期間。

對於&#x200B;**合作行銷活動**，中央實體必須指定註冊和個人化期限。

>[!NOTE]
>
>**[!UICONTROL Personalization deadline]**&#x200B;可讓中央實體選擇截止日期，本機實體必須在此日期之前傳遞檔案（試算表、影像），才能用來設定行銷活動。 這不是強制選項。 橫向步進此日期不會影響行銷活動實施。

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 客群 {#audience}

中央實體必須在建立合作行銷活動後，立即指定每個行銷活動涉及的本機實體。

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>除非已指定相關的本機實體，否則無法核准&#x200B;**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]**。

### 核准模式 {#approval-modes}

對於&#x200B;**合作行銷活動**，您可以指定訂單核准模式。

![](assets/mkg_dist_edit_kit1.png)

在手動模式下，本地實體需要訂閱行銷活動才能參與。

在自動模式中，本機實體會預先訂閱行銷活動。 它可能會取消行銷活動訂閱或修改其引數，而無需獲得中央實體的核准。

![](assets/mkg_dist_edit_kit2.png)

### 通知 {#notifications}

通知的設定與本機實體的通知相同。 請參閱[本節](creating-a-local-campaign.md#notifications)。

## 訂購行銷活動 {#ordering-a-campaign}

將合作行銷活動新增至行銷活動套件清單時，會通知屬於中央實體所定義對象的本機實體(**合作行銷活動（依目標核准）**&#x200B;沒有預先定義的對象)。 傳送的訊息包含可讓您註冊促銷活動的連結，如下所示：

![](assets/mkg_dist_mutual_op_notification.png)

此訊息也可讓本機實體檢視由建立封裝的中央運運算元輸入的說明，以及連結至行銷活動的檔案。 這些並不屬於行銷活動本身，但會提供相關的其他資訊。

一旦本機操作員透過Web介面登入，他們就能在想要訂購的合作行銷活動中輸入個人化資訊：

![](assets/mkg_dist_mutual_op_command.png)

本地實體完成註冊後，中央實體會透過電子郵件收到核准其訂單的通知。

![](assets/mkg_dist_mutual_op_valid_command.png)

如需詳細資訊，請參閱[核准程式](creating-a-local-campaign.md#approval-process)區段。

## 核准訂單 {#approving-an-order}

核准合作行銷活動套件訂單的流程，與核准本機行銷活動相同。 請參閱[本節](creating-a-local-campaign.md#approving-an-order)。
