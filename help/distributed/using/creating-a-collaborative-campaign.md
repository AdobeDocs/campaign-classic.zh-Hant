---
product: campaign
title: 建立協作行銷活動
description: 瞭解如何建立合作行銷活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Distributed Marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 4%

---

# 建立協作行銷活動{#creating-a-collaborative-campaign-intro}



中央實體會從中建立合作行銷活動 **分散式行銷** 行銷活動範本。 請參見[此頁面](about-distributed-marketing.md#collaborative-campaign)。

## 建立協作行銷活動 {#creating-a-collaborative-campaign}

若要設定合作行銷活動，請按一下 **[!UICONTROL Campaign management > Campaigns]** 節點，然後 **[!UICONTROL New]** 圖示。

>[!NOTE]
>
>除了 **[!UICONTROL collaborative campaigns (by campaign)]**，這些行銷活動可透過網頁介面設定和執行。

合作行銷活動資料庫的設定程式與本機行銷活動範本的設定程式類似。 不同型別的合作行銷活動的規格詳述如下。

### 依表單 {#by-form}

若要建立合作行銷活動（依表單），請 **[!UICONTROL Collaborative campaign (by form)]** 必須選取範本。

![](assets/mkg_dist_mutual_op_form2.png)

在 **[!UICONTROL Edit]** 索引標籤，按一下 **[!UICONTROL Advanced campaign settings...]** 連結以存取 **分散式行銷** 標籤。

選取 **依表單** 網頁介面。 此型別的介面可讓您建立個人化欄位，本機實體在訂購行銷活動時將使用這些欄位。 請參閱 [建立本機行銷活動（依表單）](examples.md#creating-a-local-campaign--by-form-).

儲存您的行銷活動。 您現在可以從以下位置使用它： **行銷活動套件** 在中檢視 **Campaign** 索引標籤中，按一下 **[!UICONTROL Create]** 按鈕。

此 **[!UICONTROL Campaign Package]** 檢視可讓您使用本機行銷活動範本（現成可用的或重複的），以及合作行銷活動的參考行銷活動，旨在為您不同的組織實體建立行銷活動。

![](assets/mkg_dist_mutual_op_form1b.png)

### 依行銷活動 {#by-campaign}

若要建立合作行銷活動（依行銷活動），請 **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** 必須選取範本。

![](assets/mkg_dist_mutual_op_by_op2.png)

訂購行銷活動時，本機實體可完成中央實體預先定義的條件，並在訂購行銷活動之前評估行銷活動。

訂購一次 **合作行銷活動（依行銷活動）** 中央實體已核准，則會為本機實體建立子行銷活動。 一旦可供它們使用，本機實體就可以修改：

* 行銷活動工作流程，
* 型別規則，
* 和個人化欄位。

本機實體會執行子行銷活動。 中央實體執行父級行銷活動。

中央實體可檢視與連結的所有子行銷活動 **合作行銷活動（依行銷活動）** 從此儀表板(透過 **[!UICONTROL List of associated campaigns]** 連結)。

![](assets/mkg_dist_mutual_op_by_op.png)

### 依據目標核准 {#by-target-approval}

若要建立合作行銷活動（透過目標核准），請 **[!UICONTROL Collaborative campaign (by target approval)]** 必須選取範本。

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>在此模式中，中央實體不需要指定本機實體。

行銷活動工作流程必須整合 **本地核准** 型別活動。 活動引數如下：

* **[!UICONTROL Action to perform]** : 目標核准通知.
* **[!UICONTROL Distribution context]** : 明確.
* **[!UICONTROL Data distribution]** ：本機實體發佈。

**本機實體分佈** 必須建立型別資料分佈。 資料發佈範本可讓您限制分組值清單中的記錄數。 在 **[!UICONTROL Resources > Campaign management > Data distribution]**，按一下 **[!UICONTROL New]** 圖示以建立新的 **[!UICONTROL Data distribution]**. 如需資料散佈的詳細資訊，請參閱 [工作流程](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) 指南。

![](assets/mkg_dist_data_distribution.png)

選取 **目標維度** 和 **[!UICONTROL Distribution field]**. 對於 **[!UICONTROL Assignment type]**，選取 **本地實體**.

在 **[!UICONTROL Distribution]** 標籤，為每個本機實體新增欄位並指定值。

![](assets/mkg_dist_data_distribution2.png)

您可以新增第二個 **目標核准** 晚於 **傳遞** 輸入activity以設定相關報表。

在行銷活動建立通知訊息中，本機實體會接收已由中央實體引數預先定義的聯絡人清單。

![](assets/mkg_dist_mutual_op_by_valid1.png)

本機實體可以根據行銷活動內容刪除某些聯絡人。

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 簡單 {#simple}

若要建立簡單的合作行銷活動，請 **[!UICONTROL Collaborative campaign (simple)]** 必須選取範本。

## 建立合作行銷活動套件 {#creating-a-collaborative-campaign-package}

若要讓本機實體可以使用行銷活動，中央實體必須建立行銷活動套件。

應用以下步驟：

1. 在 **[!UICONTROL Navigation]** 區段於 **行銷活動** 頁面，按一下 **[!UICONTROL Campaign packages]** 連結。
1. 按一下 **[!UICONTROL Create]** 按鈕。
1. 視窗頂端的區段可讓您選取 **[!UICONTROL New collaborative package (mutualizedEmpty)]** 範本。
1. 選取參考行銷活動。
1. 指定行銷活動套件的標籤、資料夾和執行排程。

### 日期 {#dates}

開始和結束日期會在行銷活動套件清單中定義行銷活動的可見度期間。

對象 **合作行銷活動**，中央實體必須指定註冊和個人化期限。

>[!NOTE]
>
>此 **[!UICONTROL Personalization deadline]** 允許中央實體選擇截止日期，本機實體必須在此日期之前傳遞檔案（試算表、影像），才能用於設定行銷活動。 這不是強制選項。 側邊步進此日期將不會影響Campaign實施。

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 對象 {#audience}

中央實體必須在建立合作行銷活動後，立即指定每個行銷活動涉及的本機實體。

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** 除非已指定相關的本機實體，否則無法核准。

### 核准模式 {#approval-modes}

對象 **合作行銷活動**，您可以指定訂單核准模式。

![](assets/mkg_dist_edit_kit1.png)

在手動模式中，本地實體需要訂閱行銷活動才能參與。

在自動模式中，本機實體會預先訂閱行銷活動。 它可以在不需要中央實體核准的情況下，取消行銷活動訂閱或修改其引數。

![](assets/mkg_dist_edit_kit2.png)

### 通知 {#notifications}

通知的設定與本機實體的通知相同。 請參閱[本節](creating-a-local-campaign.md#notifications)。

## 訂購行銷活動 {#ordering-a-campaign}

將合作行銷活動新增至行銷活動套件清單時，會通知屬於中央實體所定義對象的本機實體( **合作行銷活動（依目標核准）** 沒有預先定義的對象)。 傳送的訊息包含可讓您註冊促銷活動的連結，如下所示：

![](assets/mkg_dist_mutual_op_notification.png)

此訊息也可讓本機實體檢視建立封裝的中央運運算元輸入的說明，以及連結至行銷活動的檔案。 這些並不屬於行銷活動本身，但會提供相關的其他資訊。

一旦本地操作員透過Web介面登入，他們就可以輸入個人化資訊給想要訂購的合作行銷活動：

![](assets/mkg_dist_mutual_op_command.png)

本機實體完成註冊後，中心實體會透過電子郵件收到核准其訂單的通知。

![](assets/mkg_dist_mutual_op_valid_command.png)

如需詳細資訊，請參閱 [核准流程](creating-a-local-campaign.md#approval-process) 區段。

## 核准訂單 {#approving-an-order}

核准合作行銷活動套件訂單的流程與核准本機行銷活動相同。 請參閱[本節](creating-a-local-campaign.md#approving-an-order)。
