---
title: 同步化網頁應用程式
seo-title: 同步化網頁應用程式
description: 同步化網頁應用程式
seo-description: null
page-status-flag: never-activated
uuid: da74e4d3-e439-454a-8a43-6784e4789d1b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: df68ab11-7a8b-4e89-8cc4-8764e8a859b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 同步化網頁應用程式{#synchronizing-web-applications}

在此使用案例中，我們將使用Campaign Standard傳送通訊，其中包含Campaign v7 web應用程式的連結。 當收件者按一下電子郵件中的連結時，Web應用程式會顯示一個表格，其中包含預先載入收件者資料的多個欄位，以及電子報的訂閱連結。 收件者可以更新其資料並訂閱服務。 他的個人檔案將在Campaign v7中更新，而資訊將在Campaign standard中複製。

如果您在Campaign v7中有許多服務和Web應用程式，您可能會選擇不在Campaign standard中重新建立這些服務和Web應用程式。 ACS連接器可讓您使用所有現有的Campaign v7 web應用程式和服務，並將它們連結至Campaign standard傳送的傳送。

## 必要條件 {#prerequisites}

為達到此目的，您需要：

* 儲存在Campaign v7資料庫並與Campaign Standard同步的收件者。 請參閱同步 [配置檔案](../../integrations/using/synchronizing-profiles.md) 。
* 在Campaign v7中建立並發佈的服務和Web應用程式。
* web應用程式必須包含使 **[!UICONTROL Pre-loading]** 用識別方法的 **[!UICONTROL Adobe Campaign encryption]** 活動。

## 建立Web應用程式和服務 {#creating-the-web-application-and-service}

在Campaign v7中，您可以建立網頁應用程式，讓收件者訂閱服務。 Web應用程式和服務是設計並儲存在Campaign v7中，您可透過Campaign standard通訊來更新此服務。 若要進一步瞭解Campaign v7中的Web應用程式，請參 [閱本節](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)。

在Campaign v7中，已建立下列物件：

* 電子報服務
* 包含活動、 **[!UICONTROL Pre-loading]** a和活 **[!UICONTROL Page]** 動的Web應 **[!UICONTROL Storage]** 用程式

1. 前往並 **[!UICONTROL Resources > Online > Web applications]** 選取現有的Web應用程式。

   ![](assets/acs_connect_lp_2.png)

1. 編輯活 **[!UICONTROL Preloading]** 動。 選中 **[!UICONTROL Auto-load data referenced in the form]** 該框並選擇 **[!UICONTROL Adobe Campaign encryption]** 標識方法。 這可讓Web應用程式將表單欄位與儲存在Adobe Campaign資料庫中的資料預先載入。 請參 [閱本檔案](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

   ![](assets/acs_connect_lp_4.png)

1. 編輯 **[!UICONTROL Page]**。 已包含三個欄位（姓名、電子郵件和電話），以及一個核取方塊，邀請收件者訂閱電子報(**[!UICONTROL Newsletter]** 服務)。

   ![](assets/acs_connect_lp_3.png)

1. 前往並 **[!UICONTROL Profiles and Target > Services and subscriptions]** 開啟服 **[!UICONTROL Newsletter]** 務。 這是將從「促銷活動標準」通訊中更新的服務。 您可以看到，還沒有收件者訂閱此服務。

   ![](assets/acs_connect_lp_5.png)

1. 前往並 **[!UICONTROL Profiles and Targets > Recipient]** 選取收件者。 您可以看到他尚未訂閱服務。

   ![](assets/acs_connect_lp_6.png)

## 複製資料 {#replicating-the-data}

為了在Campaign v7和Campaign Standard之間複製所需的資料，可使用數個複製工作流程範本。 工作 **[!UICONTROL Profiles replication]** 流程會自動將所有Campaign v7收件者複製到Campaign Standard。 請參 [閱技術和複製工作流](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows)。 此工 **[!UICONTROL Landing pages replication]** 作流程可讓我們複製要在Campaign Standard中使用的Web應用程式。

![](assets/acs_connect_lp_1.png)

若要檢查資料是否已正確複製，請遵循Campaign Standard中的下列步驟：

1. 在主畫面中，按一下 **[!UICONTROL Customer profiles]**。

   ![](assets/acs_connect_lp_7.png)

1. 搜尋您的Campaign v7收件者，並檢查他是否出現在Campaign Standard中。

   ![](assets/acs_connect_lp_8.png)

1. 從頂端列，按一下 **[!UICONTROL Marketing activities]**&#x200B;並搜尋Campaign v7網頁應用程式。 它會顯示為Campaign standard的著陸頁面。

   ![](assets/acs_connect_lp_9.png)

1. 按一 **[!UICONTROL Adobe Campaign]** 下左上角的標誌，然後選取「 **Profiles &amp; audiences > Services** 」，並檢查電子報服務是否也在。

   ![](assets/acs_connect_lp_10.png)

## 設計和傳送電子郵件 {#designing-and-sending-the-email}

在本部分，我們將瞭解如何在Campaign standard電子郵件中加入連結，以連結至從Campaign v7 web應用程式複製的登陸頁面。

建立、設計和傳送電子郵件的步驟與傳統電子郵件的步驟相同。 請參閱 [Adobe Campaign Standard檔案](https://helpx.adobe.com/support/campaign/standard.html) 。

1. 建立新電子郵件，並選擇一或多個複製的個人檔案作為受眾。
1. 編輯您的內容並插入 **[!UICONTROL Link to a landing page]**。

   ![](assets/acs_connect_lp_12.png)

1. 選取從Campaign v7 web應用程式複製的著陸頁面。

   ![](assets/acs_connect_lp_13.png)

1. 準備電子郵件、傳送校樣並傳送最終電子郵件。
1. 其中一個收件者會開啟電子郵件，並按一下電子報訂閱的連結。

   ![](assets/acs_connect_lp_14.png)

1. 他新增電話號碼並檢查電子報訂閱方塊。

   ![](assets/acs_connect_lp_15.png)

## 檢索更新的資訊 {#retrieving-the-updated-information}

當收件者透過網路應用程式更新其資料時，Adobe Campaign v7會同步擷取更新的資訊。 然後，它會從Campaign v7複製到Campaign Standard。

1. 在Campaign v7中，請前往 **[!UICONTROL Profiles and Target > Services and subscriptions]** 並開啟服 **[!UICONTROL Newsletter]** 務。 您可以看到收件者現在會出現在訂閱者清單中。

   ![](assets/acs_connect_lp_16.png)

1. 前往並 **[!UICONTROL Profiles and Targets > Recipient]** 選取收件者。 您可以看到電話號碼已儲存。

   ![](assets/acs_connect_lp_17.png)

1. 在標籤 **[!UICONTROL Subscriptions]** 中，我們也可以看到他已訂閱電子報服務。

   ![](assets/acs_connect_lp_18.png)

1. 等待幾分鐘，以便運行配置檔案複製工作流。
1. 在Campaign Standard中，存取您的收件者設定檔，以檢查更新的資料是否已從Campaign v7正確複製。

   ![](assets/acs_connect_lp_19.png)

1. 編輯描述檔。 您可以看到電話號碼已更新。

   ![](assets/acs_connect_lp_20.png)

1. 按一下標 **[!UICONTROL Subscriptions]** 簽。 現在會出現電子報服務。

   ![](assets/acs_connect_lp_21.png)

