---
product: campaign
title: 同步化網站應用程式
description: 瞭解如何將Web應用程式與ACS連接器同步
feature: ACS Connector
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 1%

---

# 同步化網站應用程式{#synchronizing-web-applications}

![](../../assets/v7-only.svg)

在此使用情形中，我們將使用Campaign Standard發送一個通信，其中包括到Campaing v7 Web應用程式的連結。 當收件人按一下電子郵件中的連結時，Web應用程式將顯示一個表單，其中包含預先載入了收件人資料的多個欄位以及指向新聞簡報的訂閱連結。 收件人可以更新他的資料並訂閱該服務。 他的個人資料將在第7版市場活動中更新，資訊將以Campaign Standard複製。

如果您在市場活動v7中有許多服務和Web應用程式，則可能選擇不以Campaign Standard重新建立所有服務和Web應用程式。 ACS Connector允許您使用所有現有的市場活動v7 Web應用程式和服務，並將它們連結到Campaign Standard發送的交貨。

## 必要條件 {#prerequisites}

要實現這一點，您需要：

* 儲存在市場活動v7資料庫中並與Campaign Standard同步的收件人。 請參閱 [同步配置檔案](../../integrations/using/synchronizing-profiles.md) 的子菜單。
* 在Campaign v7中建立和發佈的服務和Web應用程式。
* Web應用程式必須包含 **[!UICONTROL Pre-loading]** 活動 **[!UICONTROL Adobe Campaign encryption]** 識別方法

## 建立Web應用程式和服務 {#creating-the-web-application-and-service}

在市場活動v7中，您可以建立允許收件人訂閱服務的Web應用程式。 Web應用程式和服務設計並儲存在Campign v7中，您可以通過Campaign Standard通信更新此服務。 要瞭解有關市場活動第7版中Web應用程式的詳細資訊，請參閱 [此部分](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)。

在「市場活動7」中，已建立以下對象：

* 新聞稿服務
* 包含 **[!UICONTROL Pre-loading]**&#x200B;的 **[!UICONTROL Page]** 和 **[!UICONTROL Storage]** 的子菜單。

1. 轉到 **[!UICONTROL Resources > Online > Web applications]** 並選擇現有Web應用程式。

   ![](assets/acs_connect_lp_2.png)

1. 編輯 **[!UICONTROL Preloading]** 的子菜單。 的 **[!UICONTROL Auto-load data referenced in the form]** 的子菜單。 **[!UICONTROL Adobe Campaign encryption]** 選擇標識方法。 這將使Web應用程式能夠用儲存在Adobe Campaign資料庫中的資料預載入表單域。 請參閱 [此文檔](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

   ![](assets/acs_connect_lp_4.png)

1. 編輯 **[!UICONTROL Page]**。 包括三個欄位（姓名、電子郵件和電話），以及一個複選框以邀請收件人訂閱新聞簡報(**[!UICONTROL Newsletter]** 服務)。

   ![](assets/acs_connect_lp_3.png)

1. 轉到 **[!UICONTROL Profiles and Target > Services and subscriptions]** 開啟 **[!UICONTROL Newsletter]** 服務。 這是將從Campaign Standard通信中更新的服務。 您可以看到尚未訂閱此服務的收件人。

   ![](assets/acs_connect_lp_5.png)

1. 轉到 **[!UICONTROL Profiles and Targets > Recipient]** 選擇收件人。 您可以看到此配置檔案尚未訂閱該服務。

   ![](assets/acs_connect_lp_6.png)

## 複製資料 {#replicating-the-data}

為了在市場活動v7和Campaign Standard之間複製所需的資料，提供了幾個複製工作流模板。 的 **[!UICONTROL Profiles replication]** 工作流將所有「市場活動v7」收件人自動複製到Campaign Standard。 請參閱 [技術和複製工作流](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows)。 的 **[!UICONTROL Landing pages replication]** 工作流支援複製我們要在Campaign Standard中使用的Web應用程式。

![](assets/acs_connect_lp_1.png)

要檢查資料是否已正確複製，請按照Campaign Standard中的以下步驟操作：

1. 在主螢幕中，按一下 **[!UICONTROL Customer profiles]**。

   ![](assets/acs_connect_lp_7.png)

1. 搜索「市場活動v7」收件人，並檢查此收件人是否顯示在Campaign Standard中。

   ![](assets/acs_connect_lp_8.png)

1. 在頂部欄上，按一下 **[!UICONTROL Marketing activities]**，並搜索Campaign v7 Web應用程式。 它顯示為Campaign Standard中的登錄頁。

   ![](assets/acs_connect_lp_9.png)

1. 按一下 **[!UICONTROL Adobe Campaign]** 徽標，在左上角，然後選擇 **配置檔案和受眾>服務** 並檢查通訊服務是否也在。

   ![](assets/acs_connect_lp_10.png)

## 設計併發送電子郵件 {#designing-and-sending-the-email}

在本部分，我們將瞭解如何在Campaign Standard電子郵件中包括連結到從市場活動v7 Web應用程式複製的登錄頁。

建立、設計和發送電子郵件的步驟與傳統電子郵件的步驟相同。 查看 [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/campaign-standard-home.html?lang=zh-Hant) 文檔。

1. 建立新電子郵件，然後選擇一個或多個複製的配置檔案作為受眾。
1. 編輯內容並插入 **[!UICONTROL Link to a landing page]**。

   ![](assets/acs_connect_lp_12.png)

1. 選擇從Campaign v7 Web應用程式複製的登錄頁。

   ![](assets/acs_connect_lp_13.png)

1. 準備電子郵件、發送校樣併發送最終電子郵件。
1. 其中一個收件人開啟電子郵件並按一下通訊訂閱的連結。

   ![](assets/acs_connect_lp_14.png)

1. 此收件人添加電話號碼並檢查新聞稿訂閱框。

   ![](assets/acs_connect_lp_15.png)

## 正在檢索更新的資訊 {#retrieving-the-updated-information}

當收件人通過Web應用程式更新其資料時，Adobe Campaignv7同步檢索更新的資訊。 然後，它將從Campaing v7複製到Campaign Standard。

1. 在Campaign v7中，轉到 **[!UICONTROL Profiles and Target > Services and subscriptions]** 開啟 **[!UICONTROL Newsletter]** 服務。 您可以看到，收件人現在出現在訂閱者清單中。

   ![](assets/acs_connect_lp_16.png)

1. 轉到 **[!UICONTROL Profiles and Targets > Recipient]** 選擇收件人。 您可以看到電話號碼已儲存。

   ![](assets/acs_connect_lp_17.png)

1. 在 **[!UICONTROL Subscriptions]** 頁籤，我們還可以看到此收件人已訂閱新聞簡報服務。

   ![](assets/acs_connect_lp_18.png)

1. 等待幾分鐘，以運行配置檔案複製工作流。
1. 在Campaign Standard中，訪問您的收件人配置檔案以檢查更新的資料是否已從市場活動v7中正確複製。

   ![](assets/acs_connect_lp_19.png)

1. 編輯配置檔案。 您可以看到電話號碼已更新。

   ![](assets/acs_connect_lp_20.png)

1. 按一下 **[!UICONTROL Subscriptions]** 頁籤。 現在將出現新聞稿服務。

   ![](assets/acs_connect_lp_21.png)
